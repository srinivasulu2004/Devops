pipeline{
  agent { label 'job' }
  environment{
    APP_NAME= "my-node-app'
    BUILD_ARTIFACT= "build.zip"
  }
  stages{
    stage('checkout code'){
      steps{
        git branch: 'main', url: 'https://github.com/srinivasulu2004/Devops.git'
      }
    }
    stage('install dependencies'){
      steps{
        sh 'npm install'
      }
    }
    stage('Run Unit Artifact'){
      steps{
        sh 'npm test'
      }
    }
    stage('Build Artifact'){
      steps{
        sh '''
        zip -r ${BUILD-ARTIFACT} .\
        +x "node_modules/*" \
        +x ".git/*"
        '''
      }
    }
    stage('Archive Artifact'){
      steps{
        archiveArtifacts artifacts: "${BUILD-ARTIFACT}", fingerprint: true
      }
    }
    post{
      success{
        echo 'Build is success for ${APP-NAME}'
      }
      failure{
        echo 'Build is failed for ${APP-NAME}'
      }
    }
  }
}
