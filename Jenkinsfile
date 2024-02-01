pipeline {
    agent any 
    
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }
    
    environment {
        SCANNER_HOME=tool 'sonar-scanner'
    }
    
    stages{
        
        stage("Git Checkout"){
            steps{
                echo '[Jenkins] Started git checkout'
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/jaiswaladi246/Petclinic.git'
                echo '[Jenkins] End git checkout'
            }
        }
        
        stage("Compile"){
            steps{
                echo '[Jenkins] Started Compiling'
                sh "mvn clean compile"
                echo '[Jenkins] End Compiling'
            }
        }
        
         stage("Test Cases"){
            steps{
                echo '[Jenkins] Started Test suite'
                sh "mvn test"
                echo '[Jenkins] End Test suite'
            }
        }
        
       
     
         stage("Build"){
            steps{
				echo '[Jenkins] Started Build suite'
                sh " mvn clean install"
				echo '[Jenkins] Ends Build suite'
            }
        }
        

        stage("Deploy To Tomcat"){
            steps{
				echo '[Jenkins] Started Deploying to Tomcat'
                sh "cp target/petclinic.war /opt/apache-tomcat-9.0.80/webapps/"
				echo '[Jenkins] Ends Deploying to Tomcat'
            }
        }
    }
}
