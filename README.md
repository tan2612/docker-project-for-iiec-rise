# docker-project-for-iiec-rise
WARNING: I'm not good at writing documentation
This project is created under iiec-rise with docker technology + rsyslog(Rocket-fast Syslog Server)

It is mainly to monitor logs of containers remotely and provide basic firewall services
Using this, you can monitor your network using centralised rsyslog server(just by one click). 
This project provides firewall services using pi-hole(not configured yet)
You can modify and add the directory to your container(make sure to have systemd) or you can use this image(image is recommended):
https://hub.docker.com/repository/docker/tanya2612/rise2020.34.6.2

Go inside the directory 'project' and run:
python2 main.py
And do the configuration according to your need

Requirements:
1. centos/systemd container
2. network connectivity from containers

Descrption of files:
1.main.py: This is python code for user interface
2.log_server.sh: This is shell script to create centralized server which will receive logs from clients
3.log_client.sh: This is shell script to create log client that will send logs to server(make sure to enter correct ip address)

To check the log files at centralized server:
cd /var/log/loghost/
ls  (You will see the directory with the name of your container id)
cd <container id> (you will see your logs)


Recommended command to create container:
docker run -it --privileged=true --name <container name> --network bridge -v project_storage rise2020.34.6.2 /usr/sbin/init

