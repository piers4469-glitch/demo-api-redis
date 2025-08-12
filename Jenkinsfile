node {
  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    sh 'docker image build -t piers4469/demo-api:latest .'
  }

  stage('Push') {
    withCredentials([
        usernamePassword(credentialsId: 'hub',
                         usernameVariable: 'USERNAME',
                         passwordVariable: 'PASSWORD')]) {
      sh 'docker login -p "${PASSWORD}" -u "${USERNAME}"'
      sh 'docker image push ${USERNAME}/demo-api:latest'
    }
  }

  stage('Deploy') {
    //withCredentials([
    //    file(credentialsId: 'kube-config',
    //         variable: 'KUBECONFIG')]) {
    //  sh 'kubectl apply -f deployment.yaml'
    //}
  }
}
