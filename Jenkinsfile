pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Webpack (for frontend JavaScript)"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests"
                echo "Integration tests"

                script {
                    env.STAGE_STATUS = "success"
                }
            }

            post {
                always {
                    emailext(
                        subject: "Tests Complete – ${env.STAGE_STATUS}",
                        body: "The tests completed – status is ${env.STAGE_STATUS}.",
                        to: 's223884634@deakin.edu.au',
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Check the quality of the code using ESLint (for JavaScript code)"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Scan the code for security defects using Snyk"

                script {
                    env.STAGE_STATUS = "success"
                }
            }

            post {
                always {
                    emailext(
                        subject: "Security Scan Complete – ${env.STAGE_STATUS}",
                        body: "The security scan completed – status is ${env.STAGE_STATUS}.",
                        to: 's223884634@deakin.edu.au',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to staging on AWS EC2"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on staging environment"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment"
            }
        }
    }
}
