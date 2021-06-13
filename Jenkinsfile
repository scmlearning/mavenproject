pipeline {
  agent any
  parameters {
        string(name: 'NAME', description: 'Please tell me your name?')
  }
  stages {
    stage('build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('print parameters'){
      steps {
                echo "Hello ${params.NAME}"
      }
    }
    
    stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }

  }
}
