@Library('MyLibs1')_
pipeline {
  agent any



 options {
    timeout(time: 60, unit: 'MINUTES')
    timestamps()
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }



 stages {

   stage('Init') {
        steps {
        
        Init()
      }
      
    }
     



   stage('Checkout') {
      steps {
          
         Checkout()
      }
    }



   stage('Build') {
      steps {
         
         Build()
      }
    }



   stage('Test') {
      steps {
        
       Test()
      }
    }    



   stage('Deploy') {
      steps {
          
         Deploy()
      }
    }
  }



 post {
    success {
      echo "SUCCESS"
    }
    failure {
      echo "FAILURE"
    }
    changed {
      echo "Status Changed: [From: $currentBuild.previousBuild.result, To: $currentBuild.result]"
    }
    always {
      script {
        def result = currentBuild.result
        if (result == null) {
          result = "SUCCESS"
        }
      }
    }
  }
}
