node {
    stage ('GIT Clone'){
        
        git changelog: false, credentialsId: 'git-pass', poll: false, url: 'https://github.com/sausarma/my-app.git'
    }
    stage ('Generate WAR file'){
        
        sh 'mvn clean package'
    }
    stage ('Create Docker Image') {
        sh 'docker build -t sausarma/tomcat .'
    }
    stage ('Deploy Code using Docker') {
        sh 'docker run -t -p 8081:8080 -d sausarma/tomcat'
    }
}

