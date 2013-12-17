# Hello World on ICME's Hadoop Cluster

1. Add the following lines to ~/.bash_profile


	HADOOP_HOME=/usr/lib/hadoop
	export HADOOP_HOME


2. Set up the folder structure

	mkdir wordcount
	mkdir wordcount/src
	mkdir wordcount/classes

3. Put the code the file *WordCount.java* into *wordcount/src*

4. Compile the Java Jar

	javac -classpath $HADOOP_HOME/hadoop-*-core.jar -d wordcount/classes wordcount/src/WordCount.java
	jar -cvf wordcount/wordcount.jar -C wordcount/classes/ .

5. Put a (few) text files into a folder called *input*

6. Put the input folder onto the HDFS

	hadoop fs -copyFromLocal input input

7. Run the MapReduce job

	hadoop jar wordcount/wordcount.jar org.myorg.WordCount input output

8. See the output

	hadoop fs -cat output/part-*

9. Before running again delete the output folder

	hadoop fs -rmr output
