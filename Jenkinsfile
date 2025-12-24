pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
                // Install dependencies
                sh 'pip install flask pytest'
            }
        }

        stage('Test') {
            steps {
                echo "Running Unit Tests on ${env.BRANCH_NAME}..."
                // Run the test file
                sh 'pytest test_app.py'
            }
        }

        stage('Deploy (Main Only)') {
            // This stage ONLY runs if we are on the 'main' branch
            when {
                branch 'main'
            }
            steps {
                echo ">>> Simulating Deploy to Production..."
                echo "Deployment Success!"
            }
        }
    }
}