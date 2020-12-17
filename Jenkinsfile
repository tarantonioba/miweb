pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Clonamos el repositorio'
                git url: 'https://github.com/tarantonioba/miweb'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaquetado mediante MAVEN'
                sh 'mvn package'
            }
        }
        stage('TOMCAT'){
            steps{
                echo 'TOMCAT'
                deploy adapters: [tomcat9(credentialsId: '3e388c0e-9dd7-4c95-88ff-6ffec9d6e1fe', path: '', url: 'http://localhost:8082')], contextPath: 'pruebaweb', war: 'target/miweb.war'
            }
        }
    
    }
    post{
        always{
            echo 'ejecuto siempre'
        }
        success{
            echo 'ejecuto si va bien'
        }
        failure{
            echo 'ejecuto cuando ha ido mal'
        }
        changed{
            echo 'ejecuto si esta ejecución no acaba en el mismo estado que la anterior ejecucion'
        }

    }
}