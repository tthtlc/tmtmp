pipeline {
    agent any

    stages {
        stage('Verify') {
            steps {
                sh 'ls'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tthtlc/tmtmp .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'docker login -u i$DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push tthtlc/tmtmp'
                }
            }
        }
    }
}



