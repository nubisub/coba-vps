pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nubisub/coba-vps.git'
        DEPLOY_DIR = '/var/www/html/coba-vps'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Clean workspace before checking out
                    deleteDir()

                    // Checkout the code from the specified GitHub repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: GIT_REPO]]])
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Update the deployment in the specified directory
                    sh "cp -r ./* ${DEPLOY_DIR}"
                }
            }
        }
    }
}
