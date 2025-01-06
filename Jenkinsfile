pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  environment {
    DPAT = credentials('docker')
  }
  stages {
    stage('git') {
      steps {
        git(url: 'https://github.com/stwomac/SDO_Flask', branch: 'main')
      }
    }

    stage('build') {
      steps {
        sh 'docker build -t womackst9/flask_app .'
      }
    }

    stage('login') {
      steps {
        sh '''
         docker login -u womackst9 -p ${env.DPAT_PSW}'''
      }
    }

  }
}
