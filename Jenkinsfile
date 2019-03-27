pipeline {
  agent {
    label 'btp'  //指定构建运行的节点
  }
  stages {
    stage('CodeCheckOut') { //定义代码检出阶段
      steps {
        echo 'CodeCheckOut' //运行代码检出阶段的具体步骤或者SCM工具，比如git
        //git(url: 'git@106.2.4.82:root/myproj.git', poll: true, branch: 'docker', changelog: true)
        
      }
    }
    stage('Build') { //定义编译阶段
      steps {
        parallel(  	//说明以下几个阶段会并行运行
          "Build": {  //定义并行阶段-构建
            echo 'build '  //运行构建命令，比如mvn
            //sh 'mvn clean install'
            
          },
          "EnvCheck-Build": { //定义并行阶段-环境检查
            echo 'checking '
            
          }
        )   //并行运行结束
      }
    }
    stage('Package') { //定义打包阶段
      steps {
        echo 'Package' //运行打包命令
      }
    }
    stage('SystemTest') { //定义系统测试阶段
      steps {
        echo 'system testing '  //运行系统测试命令
      }
    }
  }
}
