
pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'GitHub checkout successful!'
            }
        }

        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                writeFile file: 'index.html',
                    text: '<h1>Hello from GitHub Jenkins Docker CI/CD!</h1>'

                writeFile file: 'Dockerfile',
                    text: '''FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
'''

                sh 'docker build -t jenkins-nginx:v2 .'
            }
        }

        stage('Verify Image') {
            steps {
                sh 'docker images jenkins-nginx'
            }
        }
    }
}
