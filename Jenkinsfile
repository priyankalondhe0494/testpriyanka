pipeline {
    agent any
    stages {
        stage("Build") {
             steps {
                echo "Building the war"
            }
		}
		stage("Deploy to QA") {
             steps {
                echo "Deploying to QA"
            }
		}
		stage("Checkout") {
             steps {
                git url :https://github.com/priyankalondhe0494/testpriyanka
            }
		}
		stage("Pull docker image") {
             steps {
                sh 'docker pill naveenkhunteta/gorestddtest:1.0'
            }
		}
		stage("Run API test cases ") {
             steps {
                sh 'docker run -v $(pwd)/newman:/app/results naveenkhunteta/gorestddtest:1.0'
            }
		}
		stage("Publish HTML extra report") {
             steps {
                PublishHTML ([
				allowMissing:false,
				alwayslinktolastbuild:false,
				keepAll:true,
				reportDir:'newman',
				reportFiles:'gorest.html',
				reportName:'HTML Extra API Report',
				reportTitles:''
				])
            }
		}
		stage("Deploy to PROD") {
             steps {
                echo ("Deploy to PROD")
            }
		}
            
        }
    }
