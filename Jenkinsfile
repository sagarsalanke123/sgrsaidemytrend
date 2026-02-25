pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage("build") {
            steps {
                sh 'mvn clean deploy'
                                                 
           }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sagar-sonarqube-scannner'
            }

            steps {
                withSonarQubeEnv('sagar-sonar-qube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }    
    }
}

