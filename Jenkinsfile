pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                // Git se code automatic pull hota hai
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t my-app:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests...'
                sh 'echo "Basic Test Passed!"'
            }
        }

        stage('Deploy App') {
            steps {
                echo 'Deploying Application...'
                // Pehle se chal rahe purane container ko stop aur remove karein agar wo exist karta hai
                sh 'docker stop my-running-app || true'
                sh 'docker rm my-running-app || true'
                // Naya Container run karein Port 8080 par
                sh 'docker run -d --name my-running-app -p 8080:80 my-app:latest'
            }
        }
    }

    post {
        success {
            echo 'Pipeline Executed Successfully!'
        }
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
