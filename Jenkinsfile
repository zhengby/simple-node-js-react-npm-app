pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'alias cnpm="npm --registry=https://registry.npm.taobao.org \
                    --cache=$HOME/.npm/.cache/cnpm \
                    --disturl=https://npm.taobao.org/dist \
                    --userconfig=$HOME/.cnpmrc"'
                sh 'cnpm install' 
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}