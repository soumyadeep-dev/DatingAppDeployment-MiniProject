"Dating-app" Deployment Guide

This guide walks you through the process of deploying the "Dating application" application on an Amazon EC2 instance using Nginx and Docker. The application is hosted on GitHub, and the deployment involves setting up Nginx as a reverse proxy and using Docker for containerization.

Step 1: Set Up EC2 Instance on AWS

1. Launch an EC2 instance:
   - Go to the [EC2 console](https://console.aws.amazon.com/ec2/).
   - Click on "Launch Instance" and choose an Ubuntu AMI.
   - Configure instance details, storage, and security group.
   - Make sure to allow inbound traffic on port 80 in the security group settings.

2. Connect to EC2 via SSH:
   
   ssh -i "mykey.pem" ubuntu@ec2–54–197–62–157.compute-1.amazonaws.com
   
3. Run the following commands:
   
   sudo su
   apt update
   apt install git
   git clone https://github.com/soumyadeep-dev/DatingAppDeployment-MiniProject.git
   

Step 2: Setup Nginx and Docker

4. Install Nginx:
   
   sudo apt install nginx
   sudo systemctl start nginx
   sudo systemctl enable nginx
   sudo systemctl status nginx
   

5. Install Docker:
   
   apt-get install docker.io
   usermod -aG docker $USER
   newgrp docker
   sudo chmod 777 /var/run/docker.sock
   

6. Build and run Docker container:
   
   docker build -t my-dating-app .
   docker run -d --name netflix -p 8081:80 my-dating-app:latest
   

7. Open port 8081 in EC2 security group.

8. Access the application:
   - Copy the EC2 public IP.
   - Browse http://your_public_ip:8081.

