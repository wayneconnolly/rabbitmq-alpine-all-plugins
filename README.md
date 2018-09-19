# rabbitmq-alpine-all-plugins

Additions are that the following plugins are baked in. Based off rabbitmq:management-alpine. See https://hub.docker.com/_/rabbitmq/ for more usage.

Additions plugins: (message me to add more)

- rabbitmq_amqp1_0
- rabbitmq_mqtt
- rabbitmq_stomp
- rabbitmq_web_stomp

Usage:

```yaml
mq:
    ports: 
    - "1883:1883/tcp"
    - "4369:4369/tcp"
    - "5671:5671/tcp"
    - "5672:5672/tcp"
    - "8883:8883/tcp"
    - "15672:15672/tcp"
    - "15674:15674/tcp" 
    - "25672:25672/tcp"
    - "61613:61613/tcp"      
    - "61614:61614/tcp"   
    expose: 
    - "1883:1883/tcp"
    - "4369:4369/tcp"
    - "5671:5671/tcp"
    - "5672:5672/tcp"
    - "8883:8883/tcp"
    - "15672:15672/tcp"
    - "15674:15674/tcp" 
    - "25672:25672/tcp"
    - "61613:61613/tcp"  
    - "61614:61614/tcp"  
    environment:
      RABBITMQ_DEFAULT_USER: someuser
      RABBITMQ_DEFAULT_PASS_FILE: /run/secrets/RABBITMQ_DEFAULT_PASS
    secrets:
    - source: MQ_PASS
      target: RABBITMQ_DEFAULT_PASS    
    labels:
      io.rancher.scheduler.affinity:host_label: type=data
      io.rancher.container.pull_image: always  
    image: dubc/rabbitmq-alpine-all-plugins:latest
    restart: always
    stdin_open: true
    tty: true
```
