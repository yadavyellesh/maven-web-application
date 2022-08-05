pipeline{

agent any

tools{
maven 'maven3.8.2'

}
options{
timestamps()
buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5'))
}


stages{

  stage('CheckOutCode'){
    steps{
    git credentialsId: '7c47f687-0f55-4b7a-8666-6c5e2b941867', url: 'https://github.com/yadavyellesh/maven-web-application.git'

	
	}
  }
  
  stage('Build'){
  steps{
  sh  "mvn clean package"
  }
  }
/*
 stage('ExecuteSonarQubeReport'){
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
  
  stage('UploadArtifactsIntoNexus'){
  steps{
  sh  "mvn clean deploy"
  }
  }
  
  stage('DeployAppIntoTomcat'){
  steps{
  sshagent(['2adf7cc4-a3a7-4728-9c14-1be7df6e3db9']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.114.248:/opt/apache-tomcat-9.0.50/webapps/"    
  }
  }
  }
  }
  }
  */
}
stage('SendEMailNotification'){
emailext body: '''Build is Over!!

Regards,
Mithun Technologies,
9980923226''', subject: 'Build is over!!', to: 'yadavyellesh9@gmail.com'

}
