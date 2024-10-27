# Use the official GitHub Codespaces Ubuntu base image
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install JDK 21
RUN apt-get update && \
    apt-get install -y openjdk-21-jdk && \
    apt-get clean

# Set JAVA_HOME environment variable
ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# Install Node.js and npm
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs

# Install Angular CLI
RUN npm install -g @angular/cli@18

# Install PostgreSQL 16
RUN apt-get update && \
    apt-get install -y wget gnupg && \
    wget -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list && \
    apt-get update && \
    apt-get install -y postgresql-16 && \
    apt-get clean

# Expose PostgreSQL port
EXPOSE 5432

# Switch back to vscode user
USER vscode
