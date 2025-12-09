pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sarkar-s1497/wordpress-aws-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t wordpress-custom:latest docker/'
                }
            }
        }

        stage('Run Containers') {
            steps {
                script {
                    // Stop and remove existing containers first
                    sh 'docker-compose down -v --rmi all' 
            
                    // Then deploy the new stack
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}

