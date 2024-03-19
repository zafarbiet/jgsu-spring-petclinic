pipeline {
    agent any
    
    stages {
        
        stage("checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/zafarbiet/jgsu-spring-petclinic'
            }
        }
        
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        
        stage("capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
        
        stage("test") {
            steps {
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }
        }
        
        stage("coverage") {
            steps {
                jacoco()
            }
        }
    }
}
