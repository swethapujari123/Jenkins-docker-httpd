pipeline {

    agent any

    stages {

        stage('Checkout') {

            steps {

                checkout scm

            }

        }

        stage('Create HTTPD') {

            steps {

                sh '''
                docker rm -f httpd-container || true

                docker run -d \
                --name httpd-container \
                -p 8085:80 \
                httpd
                '''

            }

        }

        stage('Deploy HTML') {

            steps {

                sh '''
                docker cp index.html httpd-container:/usr/local/apache2/htdocs/index.html
                '''

            }

        }

    }

}
