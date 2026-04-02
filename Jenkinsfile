pipeline{
  agent any
  parameters{
    string(name:'SOURCE_FILE' , description:'Enter your webpage file' , defaultValue:'index.html')
    string(name:'DESTINATION_FILE', description:'Enter your path', defaultValue:'index.nginx-debian.html')
    choice(name: 'SERVICE' , choices:['nginx','apache','docker'], description: 'Enter your service name')
  }
  stages{
    stage('Build'){
      steps{
        sh """
        echo "Running Build stage"
        sudo cp ${params.SOURCE_FILE} /var/www/html/${params.DESTINATION_FILE}
        echo "Build completed"
        """
      }
    }
    stage('Deploy'){
      steps{
        sh """
          echo "Running deploy stage"
          sudo systemctl restart ${params.SERVICE}
          echo "Deploy completed"
        """
      }
    }
  }
}
