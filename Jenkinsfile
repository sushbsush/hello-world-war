pipeline {
agent none
  stages {
    stage ('build'){
      agent { label 'slaveone'}
      steps {
        sh 'pwd'
        sh 'ls'
        sh 'mvn package'
        sh 'scp -r target/hello-world-war-1.0.0.war root@172.31.7.117:/opt/tomcat/webapps'
        echo "package built"
      }
    }
    stage ('deploy'){
      agent { label 'slavetwo'}
      steps {
        sh 'sh /opt/tomcat/bin/service startup.sh'
        echo "Deployment is successful"
      }
    }
  }
}
