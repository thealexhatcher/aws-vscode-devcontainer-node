FROM amazonlinux
## SYSTEM SETUP
RUN yum update -y
RUN yum install -y sudo gcc g++ make git zip unzip tar bzip2 wget jq openssl uuid
## VSCODE USER Setup
RUN adduser vscode
RUN usermod -aG wheel vscode
RUN echo '%vscode ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers
## AWS CLI
RUN wget --quiet "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O ~/awscliv2.zip \
    && unzip ~/awscliv2.zip \
    && ./aws/install \
    && aws --version \
    && rm aws/install \
    && rm ~/awscliv2.zip
## Install nodejs v12 repo
RUN curl -sL https://rpm.nodesource.com/setup_12.x | bash -
## Install Docker 
RUN amazon-linux-extras install docker
RUN usermod -aG docker vscode
###
# VSCODE USER CONFIGURATION
###
USER vscode
WORKDIR /home/vscode 
RUN sudo yum install -y nodejs
RUN sudo npm install yarn -g