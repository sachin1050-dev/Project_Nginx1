pipeline {
    agent any
 
    stages {
 
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hello-app-1 .'
            }
        }
 
        stage('Deploy') {
            steps {
                sh '''
                docker stop hello-app-1 || true
                docker rm hello-app-1 || true
 
                docker run -d \
                  --name hello-app-1 \
                  -p 8081:80 \
                  hello-app-1
                '''
            }
        }
    }
}
