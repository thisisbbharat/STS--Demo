pipeline {
    agent any
    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/thisisbbharat/STS--Demo.git'
            }
        }
        stage('Build Jar') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Build image') {
            steps {
                sh 'docker rm -f $(docker ps -aq)'
                sh 'docker rmi -f $(docker images)'
                sh 'docker build -t demo:v1 .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 80:8080 demo:v1'
            }
        }
    }
}
