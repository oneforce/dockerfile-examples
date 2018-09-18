# Java程序制作Docker Image的例子

本例子是一个spring-boot应用，不过实际上本例子是用户所有Java应用。

## 构建Image

```bash
mvn clean package dockerfile:build
```

## 运行

普通启动，然后访问`http://localhost:8080``：

```bash
docker run -p 8080:8080 dockerfile-examples-examples-1:1.0-SNAPSHOT
```

设定JVM参数，使用`JVM_OPTS`环境变量：

```bash
docker run -p 8080:8080 -e JVM_OPTS='-Xmx128M -Xms128M' dockerfile-examples-examples-1:1.0-SNAPSHOT
```

设定System Properties，使用`JAVA_ARGS`环境变量：

```bash
docker run -p 8080:8080 -e JAVA_ARGS='-Dabc=xyz -Ddef=uvw' dockerfile-examples-examples-1:1.0-SNAPSHOT
```

提供程序运行参数，在后面直接添加即可：

```bash
docker run -p 8080:8080 dockerfile-examples-examples-1:1.0-SNAPSHOT --debug
```

## 参考文档

* [Dockerfile best practice](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
* [Docker ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint)
* [Postgres Dockerfile & script](https://github.com/docker-library/postgres/tree/3f585c58df93e93b730c09a13e8904b96fa20c58/11)
* [MySQL Dockerfile & script](https://github.com/docker-library/mysql/tree/b39f1e5e4ec82dc8039cecc91dbf34f6c9ae5fb0/8.0)
* [gosu Intall](https://github.com/tianon/gosu/blob/master/INSTALL.md)
* [Bash set命令教程](http://www.ruanyifeng.com/blog/2017/11/bash-set.html)