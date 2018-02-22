# DockerFile 分为四部分组成：基础镜像信、维护者信息、镜像操作指令和容器启动时执行指令

# 第一行必须指令基于的基础镜像 :latest 最新版本
FROM ubuntu:latest  
# 维护者信息
MAINTAINER Garrett "garrett.jordan@gmit.ie"
# 镜像的操作指令
# 格式为Run 或者Run [“executable” ,”Param1”, “param2”] 
# 每条run指令在当前基础镜像执行，并且提交新镜像。当命令比较长时，可以使用“/”换行。
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential
# 复制本地主机的（为Dockerfile所在目录的相对路径）到容器中的。
# 当使用本地目录为源目录时，推荐使用COPY。
COPY . /app
# 为后续的 RUN 、 CMD 、 ENTRYPOINT 指令配置工作目录。
WORKDIR /app
RUN pip install -r requirements.txt
# 两种格式：
# ENTRYPOINT [“executable”, “param1”, “param2”] 
# ENTRYPOINT command param1 param2 （shell中执行）。 
# 配置容器启动后执行的命令，并且不可被 docker run 提供的参数覆盖。
# 每个Dockerfile中只能有一个 ENTRYPOINT ，当指定多个时，只有最后一个起效。
# python app.py
ENTRYPOINT ["python"]
# 容器启动时执行指令
#支持三种格式： 
# CMD [“executable” ,”Param1”, “param2”]使用exec执行，推荐 
# CMD command param1 param2，在/bin/sh上执行 
# CMD [“Param1”, “param2”] 提供给ENTRYPOINT做默认参数。
# 每个容器只能执行一条CMD命令，多个CMD命令时，只最后一条被执行
CMD ["app.py"] 

