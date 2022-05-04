pipeline {
    agent any

    tools {
        maven "maven-3.5.4"
        jdk "JDK-11"
    }

    stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
            }
        }
        stage('Build') {
            steps {
                dir("${WORKSPACE}") {
                sh 'mvn -B -DskipTests clean package'
                }
            
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
   } 
}
