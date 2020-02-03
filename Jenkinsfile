pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/vipin1297/Kalyanam-UI.git'
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
             cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.30/webapps
             curl -u admin:admin http://172.31.14.219:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
