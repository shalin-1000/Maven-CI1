FROM openjdk:8 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN mkdir /app
COPY D:/CICD\ Project/20\ Projects/last_git/vprofile-project/* /app/
RUN cd /app && mvn install

FROM tomcat:8-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]