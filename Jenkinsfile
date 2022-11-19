node {
	def app
	stage('Clone repository') {
		git 'https://github.com/plum-king/PracticeOpenSource.git'
	}
	stage('Build image') {
		app = docker.build("jisoohwang/prbasedtest")
	}
	stage('Test image') {
		app.inside {
			sh 'make test'
		}
	}
	stage('Push image') {
		docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}
}
