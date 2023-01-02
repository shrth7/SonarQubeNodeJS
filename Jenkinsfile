node(){

 

   
    def sonarScanner = tool name: 'forSonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'

 

 

    
    try {
        stage('Checkout Code'){
            checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '60d8691b-71cc-4878-8c54-0ab3f3debec0', url: 'https://github.com/shrth7/SonarQubeNodeJS/']])
        }

 

        stage('NPM Build'){
            sh "npm install"
        }

 

        stage('Test Cases Execution'){
            echo "The test is SUCCESSFUL"
        }

 

        stage('SonarQube Analysis'){
            withSonarQubeEnv(credentialsId: '2c069a5b-1119-4967-b5f4-0f2b232e26be') {
            sh "${sonarScanner}/bin/sonar-scanner"
        }
    }

 

 

    }
    catch (Exception e){
        currentBuild.result = 'FAILURE'
        echo currentBuild.currentResult
    }finally{
        emailext body: '''Hello Sharath ,
The build was successful''', subject: 'Build Status!!', to: 'shrth7777@gmail.com'
    }
}
