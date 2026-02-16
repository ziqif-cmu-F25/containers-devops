FROM maven:3.8.4-jdk-8-slim

WORKDIR /app

# Copy full project source into image for an in-container build.
COPY . .

# Build a runnable Spring Boot JAR inside the container.
RUN mvn -q clean package -DskipTests && \
    JAR_FILE="$(ls target/*.jar | grep -v 'original' | head -n 1)" && \
    cp "${JAR_FILE}" /app/app.jar

# Spring Boot default port (8080).
EXPOSE 8080

CMD ["java", "-jar", "/app/app.jar"]
