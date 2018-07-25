FROM jenkins/jenkins:lts
USER root
RUN apt-get update && \
apt-get -y install apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable" && \
apt-get update && \
apt-get -y install docker-ce

RUN /usr/local/bin/install-plugins.sh blueocean:latest blueocean-bitbucket-pipeline:latest blueocean-git-pipeline:latest blueocean-github-pipeline:latest blueocean-pipeline-api-impl:latest bitbucket:latest bitbucket-approve:latest bitbucket-build-status-notifier:latest bitbucket-pullrequest-builder:latest cloudbees-bitbucket-branch-source:latest sonar:latest slack:latest
