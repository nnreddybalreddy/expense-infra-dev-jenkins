pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    stages {
        stage('Deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
        }     
        stage('Init') {
            steps {
               sh """
                cd 01-vpc
                terraform init -reconfigure

               """
            }
        }
        stage('Plan') {
            steps {
                sh 'echo This is Test'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}

