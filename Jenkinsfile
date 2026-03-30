pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/tanujatumula20/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-app:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                echo 'Stopping old container if running...'
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
            }
        }

        stage('Deploy New Container') {
            steps {
                echo 'Deploying new container...'
                sh 'docker run -d --name my-app -p 3000:3000 my-app:latest'
            }
        }

    }

    post {
        success {
            echo '✅ Deployment Successful!'
        }
        failure {
            echo '❌ Deployment Failed!'
        }
    }
}