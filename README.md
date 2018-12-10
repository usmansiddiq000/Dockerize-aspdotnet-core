#Created by Muhammad Usman
# Dockerize-aspdotnet-core
Dockerize aspdotnet core with auto migration 


Before Everything , just spin sql server docker container , with following commands.
```
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=password@123456' -p 1433:1433 -d --name sqlinux microsoft/mssql-server-linux
```

For core to connect to sql server.

```
git clone https://github.com/usmansiddiq000/Dockerize-aspdotnet-core.git
```

```
cd /Dockerize-aspdotnet-core

```
inside the project there is executable file "deploy". Run that with following command.
```
./deploy
```


it will create docker container and will spin it.

Code inside './deploy'

```
docker build -t dotnetapp .     // refrence Dockerfile inside project
docker kill dotnetContainer
docker rm dotnetContainer
docker run -d -p 5000:5000 --link sqlinux:sqlinux --name dotnetContainer dotnetapp

```
deploy file can be used for automation by adding ssh and git pull for remote server. 
