pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/shar4440/RbdgtcApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Debug Paths') {
            steps {
                sh 'echo "Current directory: $(pwd)"'
                sh 'ls -l'
                sh 'ls -l target'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar target/RbdgtcApp-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo '✅ Build and JAR executed successfully!'
        }
        failure {
            echo '❌ Build or execution failed. Check logs.'
        }
    }
}
