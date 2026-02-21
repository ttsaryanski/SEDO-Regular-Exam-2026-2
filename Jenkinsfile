pipeline{

    agent any

    stages{
        stage("Install dependencies") {
            when {
                expression { return env.GIT_BRANCH == 'origin/main' }
            }
            steps{
                bat "dotnet restore"
            }
            post {
                success {
                    echo "Dependencies installed successfully."
                }
                failure {
                    echo "Failed to install dependencies."
                }
            }
        }
        stage("Build application") {
            when {
                expression { return env.GIT_BRANCH == 'origin/main' }
            }
            steps{
                bat "dotnet build --no-restore"
            }
            post {
                success {
                    echo "Application built successfully."
                }
                failure {
                    echo "Failed to build application."
                }
            }
        }
        stage("Run tests") {
            when {
                expression { return env.GIT_BRANCH == 'origin/main' }
            }
            steps{
                bat "dotnet test --no-restore --no-build"
            }
            post {
                success {
                    echo "Tests run successfully."
                }
                failure {
                    echo "Failed to run tests."
                }
            }
        }
    }
    post {
        success {
            echo "Pipeline completed successfully."
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
