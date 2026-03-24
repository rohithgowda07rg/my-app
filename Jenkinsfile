pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/my-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {

                sh '''

                echo "Deploying app..."

                mkdir -p /home/ec2-user/app

                cp target/my-app-1.0.jar /home/ec2-user/app/app.jar

                pkill -f app.jar || true

                nohup java -jar /home/ec2-user/app/app.jar > app.log 2>&1 &

                '''

            }
        }

    }
}
