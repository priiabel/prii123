pipeline {
   agent any
tools {
    maven "MAVEN_HOME"
}
   stages {
      stage('GIT Checkout') {
         steps {
            echo 'This is GIT checkout'
            git credentialsId: 'Tomcat access', url: 'https://github.com/priiabel/prii123.git'
         }
      }
      stage('Build') {
         steps {
            echo 'This is the Build Part'
            sh '''
            cd /var/lib/jenkins/workspace/testpipe/samplemvnwar
            mvn clean package
            '''
         }
      }
      stage('Deploy') {
         steps {
            echo 'This is the Deploy Part'
            deploy adapters: [tomcat7(credentialsId: 'tomcataccess', path: '', url: 'http://13.232.136.124:9090')], contextPath: 'usingwithSCM', war: '**/*.war'
         }
      }
   }
}
