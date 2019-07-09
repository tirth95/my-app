node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.31.42:/home/ec2-user/apps/tomcat/apache-tomcat-9.0.21/webapps/'
      }
   }
 
}
