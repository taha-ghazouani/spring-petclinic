#!/usr/bin/env groovy
// shebang tells most editors to treat as groovy (syntax highlights, formatting, etc)
pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
		// The checkout stage is now implicit since we are using a Jenkinsfile
        }
        stage('Build') {
            steps {
                // To run Maven on a Windows agent, use
                bat 'set "JAVA_HOME=D:\\Java\\jdk-17.0.2\\" && .\\mvnw.cmd clean package'
            }
        }
    }
	// post pipeline actions
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
        }
        success {
            archiveArtifacts 'target/*.jar'
        }
    }
}
