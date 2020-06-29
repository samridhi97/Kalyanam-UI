pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/samridhi97/Kalyanam-UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			ng build --base-href=/matrimony/                      
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/dist/matrimony /webapps
             docker cp jen_mvn:$WORKSPACE/dist/matrimony .
             docker cp matrimony tommcat1:/usr/local/tomcat/webapps
             curl -u admin:admin http://3.16.152.195:8083/manager/reload?path=/matrimony
             '''
		}
	}
}
}
