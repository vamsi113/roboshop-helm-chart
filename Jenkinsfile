pipeline {
    agent any
    parameters {
        string(name: 'component', defaultValue: '', description: 'Component Name')
        string(name: 'appVersion', defaultValue: '', description: 'Component appVersion')
    }



    stages {

        stage('Check Out Application code') {
            steps {
                dir('APP') {
                   git branch: 'main', url: 'https://github.com/vamsi113/${component}.git'
                }

            }
        }
        stage('Helm Deploy') {
            steps {
                sh '''
                    helm install ${component} . -f APP/helm/prod.yml
                '''
            }
        }

    }
}
