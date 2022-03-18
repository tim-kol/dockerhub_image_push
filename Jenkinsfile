pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('timkol_dockerhub_credentials')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t timkol1411/automate_nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push timkol1411/automate_nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}