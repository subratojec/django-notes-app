@Library("shared") _
pipeline {
    agent { label "docker-agent" }
    stages {
        stage('code') {
            steps {
                script {
                    clone("https://github.com/subratojec/django-notes-app", "main")
                }
            }
        }
        stage('build') {
            steps {
                script {
                    docker_build("notes-app", "latest", "subrato123")
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                echo "Pushing To DockerHub"
                script {
                    docker_push("notes-app", "latest", "subrato123")
                }
            }
        }
        stage('deploy') {
            steps {
                echo "This is deploying the code."
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
