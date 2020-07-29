pipeline {

    agent any
    tools {
        maven 'apache-maven-3.6.3' 
    }
        stages{
        stage('compile') {
            steps{
   
       bat 'mvn compile'
 
            }
  }
               stage('test') {
            steps{
   
       bat 'mvn test'
 
            }
  }
            
            //arti
            stage('arti'){
                steps{
                archiveArtifacts artifacts: 'pom.xml, */*.war', followSymlinks: false
                }
            }
            
                   stage('SonarQube analysis') {
           steps{
    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
        
        bat 'mvn sonar:sonar'
         }
       }
  }
        }
    
    }
