pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/prohodec/test_jenkins_rep.git']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/prohodec/test_jenkins_rep.git'
                sh 'python3 app.py'
            }
        }
        stage('SonarQube Analysis') {
    steps {
        script {
            def scannerHome = tool 'sonar'
            withSonarQubeEnv('SonarQubeServer') {
                sh "${scannerHome}/bin/sonar-scanner"
            }
        }
    }
}

    }
}