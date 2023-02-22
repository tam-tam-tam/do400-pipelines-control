pipeline {
	agent {
		node {
			label 'nodejs'
		}
	}
	parameters {
		booleanParam(name: "RUN_FRONTEND_TESTS", defaultvalue: true)
	}
	stages {
		stage('Run Tests') {
			parallel {
				stage('Backend Tests') {
					steps {
						sh 'node ./backend/test.js'
					}
				}	
				stage('Frontend Tests') {
					when { expression { params.RUNFRONTEND_TESTS } }
					steps {
						sh 'node ./frontend/test.js'
					}
				}
			}
		}
	}
}
