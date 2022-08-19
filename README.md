# ValidateOidTest
# Automation Developer - Technical Assignment-Solution

## Test Target

The test target is a CLI program that determines if a given SNMP trap starts with any of the prefixes.

The list of prefixes for which to filter is fixed for a given run and will normally contain several hundred entries.


Below is sample of SNMP prefixes to be validated against:
```
trap-type-oid-prefix:
  - .1.3.6.1.6.3.1.1.5
  - .1.3.6.1.2.1.10.166.3
  - .1.3.6.1.4.1.9.9.117.2
  - .1.3.6.1.2.1.10.32.0.1
  - .1.3.6.1.2.1.14.16.2.2
  - .1.3.6.1.4.1.9.10.137.0.1
```
### Framework

The Automation Framework is built using Maven/Java/TestNG with PageObjectModel design pattern. The framework has the following package/artifact setup:
 
 ![image](https://user-images.githubusercontent.com/111313561/185711698-9f504f1b-71c3-4b79-8250-4c32a07cf5f4.png)


In the current solution no UI is involved so the automation.pages is empty; however, this framework can be extended to UI automation too.

### Pre-requisites:

1.	Install Java(version 8 or beyond) and setup Java_Home environment variable
2.	Install Maven and setup Maven_Home environment variable


### Setup and Instructions:

1.	The project can be downloaded from github, Unzip and open in your favorite IDE.
2.	This is a Maven project so IDE needs Maven plugin (Most of the IDE's have this plugin by default)
3.	The POM.xml included in the project has all the dependencies needed to run this project.
4.	4.Install TestNG plugin in the IDE.


### Test Data:

The project comes with reference data and test data files; however, the user can modify the input he wants to specify for each test case.

1.	The reference data is located in automation.referencedata package.(SNMPPrefix.txt and SNMPLargeFile.txt)
2.	The test data properties file is located in automation.testdata package (testData.properties)

**Test cases :**

The Automation suite has functional test cases to validate the positive and negative tests and a performance test to get process time for large file.

**Functional Test Suite:**

1.	Verify that an OID has a valid prefix, contains one of the expected prefixes.
2.	Check for an empty/blank OID.
3.	Verify the first character starts with a '.'.
4.	Check if last character is numeric.
5.	Verify the pattern matches the prefix.
6.	Check for maximum length of the OID (assuming it is no longer than 128 characters).
7.	Check for an Invalid descendant meaning the OID matches the prefix but has invalid characters after that.
8.	Check for valid descendant to check if OID has valid characters and pattern after the expected prefix.
9.	Verify Exact match condition.


**Performance Test case:**

1.Record the runtime to process large file and log it to the report.

**Error handling:**

Both Hard asserts and soft asserts are implemented in test cases. The soft asserts to pass the test case even of failure, however the reports have a log that explains it.

**Reports:**

By default the testNG reports are saved in \\test-output\Default suite folder.


**Running the test suite:**

The tests can be run individually or as a suite. The testng.xml in the project can be used to trigger all tests in the suite.
To run the tests from CLI using maven , Navigate to the project folder where the pom.xml resides.

Enter the command $ mvn test to run the entire suite.

To run the test case individually follow below steps:

1.	Open the project in the IDE, open the ValidateOidTest.java from automation.tests package
2.	Select the test, right click, and select Run as TestNG test.


**Advanced options:(Not covered in this solution)**

To run this as part of CI/CD , we can create a runnable jar and execute it as a part of build deployment.

Build a docker image and utilize it for setting up in CI/CD process.
