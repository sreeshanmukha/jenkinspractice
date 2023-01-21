pipeline
{
    agent any
    stages 
    {
        stage('ContinuousDownload')
        {
            steps 
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
            
        stage('ContinuousBuild')
        {
            steps 
            {
                sh 'mvn package'
            }
        }
        
         stage('ContinuousDeployment')
        {
            steps 
            {
                deploy adapters: [tomcat9(credentialsId: 'a1cd787b-ef23-4250-964c-f82a64fab38e', path: '', url: 'http://172.31.39.241:8080')], contextPath: 'testapp2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps 
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarative1/testing.jar'
            }
        }
        
         stage('ContinuousDelivery')
        {
            steps 
            {
                deploy adapters: [tomcat9(credentialsId: 'a1cd787b-ef23-4250-964c-f82a64fab38e', path: '', url: 'http://172.31.33.124:8080')], contextPath: 'prodapp2', war: '**/*.war'   
            }
        }
    }    
}

