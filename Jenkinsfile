pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-app")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop old container if running
                    sh "docker stop flask-app || true"
                    sh "docker rm flask-app || true"

                    // Run new container
                    sh "docker run -d -p 5000:5000 --name flask-app flask-app"
                }
            }
        }
    }
}
