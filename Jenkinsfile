pipeline {
    agent {
        docker {
            image 'maven:3.9.5-eclipse-temurin-17'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Running automation tests...'
                bat 'mvn test'
            }
        }
    }
    post {
        always {
            echo 'Archiving test results...'
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
