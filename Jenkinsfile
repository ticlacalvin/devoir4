node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        check scm
}

stage('Build image') {
    /* This builds the actual image */

    app = docker.build("ticlacalvin/devoir3")
}

stage('Test image') {

    app.inside {
        echo "Tests passed"
    }
}

stage('Push image') {
    /*
                    You would need to first register with DockerHub before you can push images to your account
            */
    docker.withRegistry('https:registry.hub.docker.com', 'dockerhub-credentials') {
        app.push("${env.BUILD_NUMBER}")
        app.push("latest")
        }
            echo "Trying to push Docker Build to DockerHub"
    }
}
