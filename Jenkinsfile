pipeline {
    agent { label 'GOL'}
    triggers {
        cron('H * * * *')
        pollSCM('* * * * *')
    }
    stages {
        stage('scm') {
            steps {

                git branch: 'master', url: 'https://github.com/asquarezone/game-of-life.git'
                input 'Continue to next stage? '
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
    }
    post {
        success {
            archive '**/gameoflife.war'
            junit '**/TEST-*.xml'
        }
        
    }
}