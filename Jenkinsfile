pipeline {
    agent any
	
	    stages {
        stage('Clone code from SCM') {
            steps {
                echo 'Get code from GITHUB SCM'
				git branch: 'main', url: 'https://github.com/rsandeep47/JavaApp1.git'
            }
        }
		stage('Build Artifact') {
            steps {
                echo 'Build Artifact using maven'
				sh 'mvn clean install'
            }
        }
		stage('Deploy') {
            steps {
                echo 'Deployed on Tomcat'
				deploy adapters: [tomcat9(credentialsId: 'TomcatCredntials', path: '', url: 'http://18.208.217.74:8081/')], contextPath: 'JavaApp', war: '**/*.war'
            }
        }
    }
}
