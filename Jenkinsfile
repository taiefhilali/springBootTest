pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerHub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t taiefhilali/devopsimage .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push taiefhilali/devopsimage'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}


// pipeline {
//     agent any
    
//     stages {
//         stage('Checkout GIT') {
//             steps {
//                 echo 'Pulling...'
//                 git branch: 'main', url: 'https://github.com/taiefhilali/springBootTest.git'
//             }
//         }
//     }
// }
