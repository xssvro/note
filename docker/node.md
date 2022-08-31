# Docker Note

> 主要参考资料：《深入浅出Docker@》[英] 奈吉尔•波尔顿（Nigel Poulton）

## 容器命令
1. **docker container run** 是启动新容器的命令。该命令的最简形式接收镜像和命令作为参数。镜像用于创建容器，而命令则是希望容器运行的应用。docker container run -it ubuntu /bin/bash 命令会在前台启动一个Ubuntu容器，并运行Bash Shell。
2. **docker container ls** 用于列出所有在运行（UP）状态的容器。如果使用-a 标记，还可以看到处于停止（Exited）状态的容器。
3. **docker container exec** 允许用户在运行状态的容器中，启动一个新进程。该命令在将Docker主机Shell连接到一个运行中容器终端时非常有用。**docker container exec -it \<container-name or container-id\> bash** 命令会在容器内部启动一个Bash Shell进程，并连接到该Shell。为了使该命令生效，用于创建容器的镜像必须包含Bash Shell。
4. **docker container stop** 命令会停止运行中的容器，并将状态置为Exited(0) 。该命令通过发送SIGTERM信号给容器内PID为1的进程达到目的。如果进程没有在10s之内得到清理并停止运行，那么会接着发送SIGKILL信号来强制停止该容器。docker container stop 可以接收容器ID以及容器名称作为参数。
5. **docker container start** 会重启处于停止（Exited）状态的容器。可以在docker container start 命令中指定容器的名称或者ID。
6. **docker container rm **会删除停止运行的容器。可以通过容器名称或者ID来指定要删除的容器。推荐首先使用docker container stop 命令停止容器，然后使用docker container rm 来完成删除。
7. **docker container inspect** 命令会显示容器的配置细节和运行时信息。该命令接收容器名称和容器ID作为主要参数。