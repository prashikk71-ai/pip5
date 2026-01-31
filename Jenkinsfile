pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['QA', 'UAT'],
            description: 'Pick Environment value'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '/home/prashik/Downloads/apache-maven-3.9.12/bin/mvn clean install'
            }
        }

        stage('Deployment') {
            steps {
                script {
                    if (params.ENVIRONMENT == 'QA') {
                        sh 'cp target/pip5.war /home/prashik/Downloads/apache-tomcat-11.0.15/webapps'
                        echo "Deployment has been done on QA!"
                    }
                    else if (params.ENVIRONMENT == 'UAT') {
                        sh 'cp target/pip5.war /home/prashik/Downloads/apache-tomcat-11.0.15/webapps'
                        echo "Deployment has been done on UAT!"
                    }
                }
            }
        }
    }
}
