pipeline {
	agent any
	stages {
		stage("Compile") {
			steps {
				sh "./gradlew compileJava"
			}
		}
		stage("Unit test") {
			steps {
				sh "./gradlew test"
			}
		}
		stage("Code coverage") {
			steps {
				sh "./gradlew jacocoTestCoverageVerification"
				sh "./gradlew jacocoTestReport"
				publishHTML ([
					allowMissing: false, 
					alwaysLinkToLastBuild: false, 
					keepAll: true, 
					reportDir: 'build/reports/jacoco/test/html',
					reportFiles: 'index.html',
					reportName: "Jacoco Report",
					reportTitles: 'Jacoco Report'
				])				
			}
		}
		stage("Static code analysis") {
			steps {
				sh "./gradlew checkstyleMain"
				publishHTML ([
					allowMissing: false, 
					alwaysLinkToLastBuild: false, 
					keepAll: true, 
					reportDir: 'build/reports/checkstyle/',
					reportFiles: 'main.html',
					reportName: "Checkstyle Report",
					reportTitles: 'Checkstyle Report'
				])

			}
		}
	}
}
