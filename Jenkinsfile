pipeline{

agent any
stages{
stage ('backup')
{
steps{
  sh '''
     cd /var/lib
     zip -r ${WORKSPACE}/backup.zip jenkins	 
  '''

}


}
stage ('upload file into s3 bucket')
{
steps{
  script{
  s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'devopsdemo2025', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '*.zip', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'demo', userMetadata: []
  }

}

}

}
}
