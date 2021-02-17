# preparing-kafka-apps

## How to work with Kafka producers and consumers?
1. Make sure you have maven and openjdk isinstalled in your PC.
2. Install Kafka from [link](https://kafka.apache.org/quickstart)
3. Unzipping kafka:
```
 * Unzip the tar file using 7-zip extracter 
 * Un-tar it (using Bash) and change into the directory. command: tar -xzf <filename>
```
4. Set environment variables as below:
```
 * JAVA_HOME = C:\Program Files\OpenJDK\jdk-version folder
 * KAFKA_HOME =  C:\kafka-version folder
 * M2_HOME = C:\ProgramData\chocolatey\lib\maven\apache-maven-version
 * Path - must include (make sure you have only one JDK location in your path!)
 * %JAVA_HOME%\bin OR C:\Program Files\OpenJDK\jdk-version\bin (or similar, NOT both!)
 * %M2_HOME%\bin
 * %KAFKA_HOME%\bin
 * %KAFKA_HOME%\bin\windows
```
 5. Run Kafka commands as below in 4 individual powershell window from the location where kafka is placed:
```
  * Run Zookeeper Service  (keep window open): .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
  * Run Kafka Service (keep window open): .\bin\windows\kafka-server-start.bat .\config\server.properties
  * Execute One-Time Commands-create: .\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic any-selected-topic
  * listing all topics you created: .\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --list    
  * Run Kafka Producer (will provide a > prompt for writing messages): .\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic any-selected-topic
  * Run Kafka Consumer (to show messages from the beginning): .\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic bearcat-messages --from-beginning
```
### Suggestion:
* If you wish to delete any topics which was created completely, run command: 
* `.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --delete --topic any-selected-topic`
* And Delete folders from C:\tmp\kafka-logs and C:\tmp\zookeeper in order to avoid any errors.
