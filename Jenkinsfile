pipeline {
    agent {label 'docker-maven'}
    stages {
		    stage('SCM Checkout') {
		    steps{
			  checkout scm
		}		
		}
        stage('Build') {
				steps {
                sh 'mvn -DskipTests clean package'
            }
        }
		
		stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
           
    }
}
