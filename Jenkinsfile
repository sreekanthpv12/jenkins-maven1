pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/myorg/myrepo.git'
            }
        }
        
        stage('Build') {
            steps {
                withMaven(maven: 'Maven 3.8.3') {
                    sh 'mvn clean install'
                }
            }
        }
        
        stage('Unit Test') {
            steps {
                withMaven(maven: 'Maven 3.8.3') {
                    sh 'mvn test'
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                withMaven(maven: 'Maven 3.8.3') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
