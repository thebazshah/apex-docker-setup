# Running Oracle Apex on Docker Containers

## Downloading Docker images for running Oracle DB, Oracle ORDS and Oracle Apex (optional)
There are two images needed to run the set up. We can optionally download the images beforehand. If images are not downloaded, they will be downloaded automatically. Following images are needed:
1. container-registry.oracle.com/database/free:latest
2. container-registry.oracle.com/database/ords-developer:latest

Run the following commands to download the images:
```
docker pull container-registry.oracle.com/database/free:latest
docker pull container-registry.oracle.com/database/ords-developer:latest
```

## Creating the containers
Whether images are downoaded or not, finally run the following command:
```
docker-compose up
```
This will start following three containers:
1. Oracle Database
2. Oracle ORDS and Oracle Apex

Pressing `Ctrl+C` will terminate the containers but it will not delete them. Moreover, the command will keep running inside terminal and will print log. When terminal exits, containers will also terminate. In order to run containers in background, use following command.
```
docker-compose up -d
```
And to terminate/delete containers, use following command.
```
docker-compose down
```

## Checking ORDS Logs
Oracle Database Engine takes some time to initialize. There are health checks in `docker-compose.yml` file which prevents ORDS/Apex container to start before database engine completes initialization. After database container is declared healthy, ORDS/Apex container starts. ORDS/Apex log can be viewed using following command.
```
docker exec -it apex-ords tail -f /tmp/install_container.log
```

## Accessing the Containers
By default the Oracle Database is exposed on port 1521 and Oracle ORDS/Apex is exposed on port 8181. Oracle ORDS/Apex can be accessed by opening http://localhost:8181 in a web browser. For the first time we can use following credentials to access Oracle Apex.
- Workspace: internal
- User:      ADMIN
- Password:  Welcome_1