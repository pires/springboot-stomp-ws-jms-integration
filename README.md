## Prerequisites

One must have ```docker``` installed.

If you're on Mac OS X, run:

```
boot2docker stop
VBoxManage modifyvm "boot2docker-vm" --natpf1 "stomp,tcp,,61613,,61613";
VBoxManage modifyvm "boot2docker-vm" --natpf1 "openwire,tcp,,61616,,61616";
boot2docker start
```

### Build amq-docker

```
git clone https://github.com/pires/amq-docker.git
cd amq-docker
docker build -t amq:5.10.0 .
```

### Run broker

```
docker run --name amq1 -p=61613:61613 -p=61616:61616 -d -t amq:5.10.0
```

## Build & run

```
git clone https://github.com/pires/springboot-stomp-ws-jms-integration.git
```

```
cd springboot-stomp-ws-jms-integration/master
mvn spring-boot:run
```

```
cd cd springboot-stomp-ws-jms-integration/minion
mvn spring-boot:run
```

## Test

Point your browser to ```http://localhost:8080``` and send a message. Should receive two greetings (one from master, another from minion).
