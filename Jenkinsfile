pipeline {
    agent any
     tools {
            maven 'Maven3'  // Ensure Maven is installed
            jdk 'JDK21'     // Ensure JDK 21 is installed
        }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/zahra-hazara/TimeCalculator1.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
