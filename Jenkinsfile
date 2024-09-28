@Library("shared") _
pipeline {
    agent { label 'vinod' }

    stages {
        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }
        stage("Cloning Code") {
            steps {
                script {
                    gitclone("https://github.com/srdangat/django-notes-app.git", "main")
                }
            }
        }
        stage("Build Docker Image") {
            steps {
                script {
                    build("notes-app", "latest", "srdangat")
                }
            }
        }
        stage("Push Image to Docker Hub") {
            steps {
                script {
                    push("notes-app", "latest", "srdangat")
                }
            }
        }
        stage("Remove Docker Images"){
            steps{
                script{
                    removeDockerImages()
                }
            }
        }
        stage("Deploy App") {
            steps {
                script{
                    manageDocker()
                }
            }
        }
    }
}
