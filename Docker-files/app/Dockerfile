FROM maven:3.9.9-eclipse-temurin-17 AS BUILD_IMAGE 
RUN git config --global http.sslVerify false
RUN  git clone https://github.com/saurabhkulkarni12/productcrudapp.git
RUN cd productcrudapp && git checkout containers && mvn install
 
FROM tomcat:9.0.62
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE productcrudapp/target/productcrudapp.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
