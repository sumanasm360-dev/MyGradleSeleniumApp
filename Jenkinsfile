pipeline {
    agent any

    tools {
        gradle 'Gradle-9'
        jdk 'JDK-17'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sumanasm360-dev/MyGradleSeleniumApp.git'
            }
        }

        stage('Debug Versions') {
            steps {
                sh '''
                    echo "JAVA VERSION:"
                    java -version

                    echo "GRADLE VERSION:"
                    ./gradlew -v
                '''
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Run Application') {
            steps {
                sh './gradlew run'
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
