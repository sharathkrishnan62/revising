pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    ./venv/bin/pip install --upgrade pip
                    ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    ./venv/bin/pip install pytest
                    ./venv/bin/pytest
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mkdir -p build
                    cp app.py requirements.txt build/
                    tar -czf flask-app.tar.gz -C build .
                '''
            }
        }
    }
}