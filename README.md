# Weather Alert Application

## Overview
This distributed application uses the [Open Weather API](https://openweathermap.org/api) to deliver real-time, reliable weather information, including immediate alerts for extreme conditions, short-term forecasts, and long-term trends. To maintain data consistency and easy access, it utilizes [Docker](https://www.docker.com/) containers for deployment, [Kafka](https://kafka.apache.org/) for real-time data streaming, and a [Python](https://www.python.org/) pipeline to process weather data, which is stored in a [MongoDB](https://www.mongodb.com/) database for analysis.


 
  ## Project Map
  
Using a combination of [Open Weather API](https://openweathermap.org/api), Python, Kafka, and MongoDB, this application builds a comprehensive machine learning pipeline for data collection, processing, analysis, visualization, and delivery. The pipeline gathers data with Open Weather API, processes and analyzes it with Python, stores it in MongoDB, and transmits updates to users through Kafka.
 

 
 ## Manual Setup

<blockquote> <p dir="auto">You can avoid this configurational step by using the <a href="#docker-setup">Docker installation process</a>.</p></blockquote>

Perform the following steps:

1- Download and install <a href="https://nodejs.org/en/">Node.js</a>.<br/>
2- Download and install <a href="https://www.python.org/">Python (>= 3.9)</a>.<br/>
3- Download and install <a href="https://nodejs.org/en/">Kafka</a>.<br/>
4- Download and install <a href="https://www.mongodb.com/">Mongodb (6.0)</a>.<br/>
5- Download and install <a href="https://kafka.apache.org/">Visual Studio Code(VS Code)</a>.<br/>
6- Install <strong>Vetur, Better Comments, Docker, Python, GitHub Theme </strong> extensions for VS Code To enjoy the code.<br/>
7- Clone this repository.<br/>
8- Connect to the MongoDB 6.0 server by running the following command:

```
mongosh mongodb://localhost:27017
```
9- Navigate to the Kafka installation directory using the "cd" command. For example, if you installed Kafka in "<strong>C:\kafka_2.13-2.8.1</strong>", type the following command and press enter:
```
cd C:\kafka_2.13-2.8.1
```
Start the ZooKeeper server (if not already running) by entering the following command:
```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```
In a separate command prompt window, start the Kafka broker by entering the following command:
```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

10- Start The Express Server:<br> <br>
Update the <code>line 14 </code>
```
mongodb://root:example@localhost:27017/mydatabase?authSource=admin
```
 Enter the following commands:
```
cd backend
npm install
node index.js
```
11- Start The Vue app by entering the following commands:
```
cd frontend
npm install
npm run serve
```
12- Start The Analysis server by entering the following commands:
```
cd analysis-servers
pip install --no-cache-dir -r requirements.txt
python daily-analytics.py
```
13- Start The Alert server by entering the following commands:
```
cd alert-server
pip install --no-cache-dir -r requirements.txt
python alert-server.py
```
14- Start The Collect server by entering the following commands:
```
cd collect-server
pip install --no-cache-dir -r requirements.txt
python collect-server.py
```
Now, You can now access the server at http://localhost:8080/.

<h2 tabindex="-1" dir="auto"><a id="user-content-docker-setup" class="anchor" aria-hidden="true" href="#docker-setup"></a>Docker Setup</h2>
<blockquote>
<p dir="auto">Make sure Docker is installed.</p>
</blockquote>
<p dir="auto">Spin up the containers</p>

```
docker-compose up -d --build
```
Running the command will expose 7 services with the following ports:
<ul dir="auto">
<li><strong>Alert-server</strong> - <code>:9000</code></li>
<li><strong>Analysis-server</strong> - <code>:8000</code></li>
<li><strong>Backend</strong> - <code>:3000</code></li>
<li><strong>Frontend</strong> - <code>:8080</code></li>
<li><strong>Kafka</strong> - <code>:9092|9094</code></li>
<li><strong>Zookeeper</strong> - <code>:2181</code></li>
<li><strong>Mongodb</strong> - <code>:27017</code></li>
</ul>

You can now access the server at http://localhost:8080/.
