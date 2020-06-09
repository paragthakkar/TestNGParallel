# TestNGParallel

TestNG Parallel Test Execution Demo

Commands to create a Hub and Nodes network : 

1. Create a Docker Network
```
docker network create grid
```

2. Create a Hub in the network
```
docker run -d -p 4444:4444 --net grid --name selenium-hub selenium/hub:3.11.0-dysprosium
```

3. Create two nodes, a Chrome and other for Firefox
```
docker run -d -P -p 5900:5900 --net grid -e HUB_HOST=selenium-hub -v /dev/shm:/dev/shm selenium/node-chrome-debug:3.11.0-dysprosium
docker run -d -P -p 5901:5900 --net grid -e HUB_HOST=selenium-hub -v /dev/shm:/dev/shm selenium/node-firefox-debug:3.11.0-dysprosium
```

4. Verify the 3 nodes are running
```
docker ps
```

So, the Hub and Nodes are ready, just clone the repo and hit run!
