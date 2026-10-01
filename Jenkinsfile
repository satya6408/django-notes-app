@Library('shared') _

pipeline {

    agent {
        label 'vinod'
    }

   
    stages {
         
         stage('Hello') { 
             steps {
                 script {
                     hello()
                     }
                 }
        }
        stage('Code') {
            steps {
                echo 'This is cloning the code'
                script{
                    clone('https://github.com/satya6408/django-notes-app.git','main')
                    echo 'Code cloning successfully'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'This is building the code'
                    script{
                        docker_build("notes-app","latest","satya6408")     
                        }
            }            
        }

        stage('Push To DockerHub') {
            steps {
                echo 'This is pushing the image to Docker Hub'
                script{
                        docker_push("notes-app","latest","satya6408")
                }    
                    
            }
        }

        stage('Deploy') {
    steps {

        script {
                    docker_compose()
        }
    }
}
    }
}
