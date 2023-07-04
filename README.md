# Performance-testing-java-workshop
Performance Testing Java workshop

In this workshop, we'll discuss performance testing basics, and run some demos to show you how to get started running and testing an application.

** You will need to install this software, please do it before the lab if possible **

Clone:
[https://github.com/spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic)

Install Zulu 17:

[https://www.azul.com/downloads/?package=jdk#zulu](https://www.azul.com/downloads/?package=jdk#zulu)

Set it to be the  JVM:

export JAVA_HOME=`/usr/libexec/java_home -v 17.0.7`

OR

export JAVA_HOME=/Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home

Download and unpack JMETER:
[https://jmeter.apache.org/download_jmeter.cgi](https://jmeter.apache.org/download_jmeter.cgi)

Download and install VisualVM:

[https://visualvm.github.io/download.html](https://visualvm.github.io/download.html)

Download HistogramLogAnalyzer from this workshop’s project folder

([https://github.com/prpatel/Performance-testing-java-workshop](https://github.com/prpatel/Performance-testing-java-workshop))

Download the built Spring Boot app from the link below
https://drive.google.com/file/d/1-J1sXzRMmtbDK4pVpwdWcTcZHWXRtCdz/view?usp=sharing

Start everything up, remember to set the JVM as described above

Run Spring boot app:
Download JAR file from:
https://drive.google.com/file/d/1-J1sXzRMmtbDK4pVpwdWcTcZHWXRtCdz/view?usp=sharing
(building it downloads too many test related things like Docker containers)

java -Xmx64m '-Xlog:gc*=debug:file=test_zulu_17.log' -javaagent:../jHiccup-2.0.10/jHiccup.jar -jar target/spring-petclinic-3.1.0-SNAPSHOT.jar

start Jmeter:

./jmeter -t ../../spring-petclinic/src/test/jmeter/petclinic_test_plan.jmx

start VisualVM

(use the installed version, it is an application)

start HistogramLog Analyzer:

java -jar target/HistogramLogAnalyzer-1.0.4-SNAPSHOT.jar

start GC log analyzer

 java -jar GCLogAnalyzer2.jar &

- Run the Jmeter test for a few mins

Log files will be in the directory where you started the Spring Boot App.

- hiccup.log with the HistogramLogAnalyzer
- test_zulu_17.log with the GCLogAnalyzer
