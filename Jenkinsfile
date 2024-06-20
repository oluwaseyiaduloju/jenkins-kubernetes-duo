pipeline {
    agent any
    stages {
        stage('Deploy App') {
            steps {
                sh "kubectl apply -f app-config.yaml"
                sh "kubectl apply -f flask-app.yaml"
            }
        }
        stage('Deploy NGINX') {
            steps {
                sh "kubectl apply -f nginx-config.yaml"
                sh "kubectl apply -f nginx.yaml"
                sh "sleep 50"
                sh "kubectl get svc flask-app"
                sh "kubectl get svc nginx-service"
                sh "sleep 100"
                sh "kubectl delete -f ."
            }
        }
    }
}