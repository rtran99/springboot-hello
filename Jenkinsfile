pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {
                // Run Maven on a Unix agent.
                sh "mvn clean compile"
            }
        }
        stage('Build Docker image'){          
            steps {
                echo "Hello Java Express"
                sh 'ls'
                sh 'docker build -t ronytran/docker_jenkins_springboot:${BUILD_NUMBER} .'
            }
        }
        stage('Docker deploy'){
            steps {               
                sh 'docker run -itd -p  8081:8080 ronytran/docker_jenkins_springboot:${BUILD_NUMBER}'
            }
        }
    }
}
