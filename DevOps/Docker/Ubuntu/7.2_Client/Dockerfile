FROM ubuntu:14.04

# 1. Use your own e-mail for the maintainer.
MAINTAINER jamescoulter@thinkboxsoftware.com

# Perform a general udpate of the OS.
RUN apt-get update && apt-get -y upgrade

# Add requirements for Deadline 7 headless Slave.
RUN apt-get update && apt-get install -y libgl1-mesa-glx libglib2.0-0

# Copy over the installer.
# 2. Be sure the installer .run file has been placed in the same folder as the Dockerfile.
RUN mkdir /thinkboxsetup/
COPY DeadlineClient-7.*-linux-x64-installer.run /thinkboxsetup/

# Run the installer.
# 3. Replace the name of the license server after --licenseserver below with that of your actual license server.
RUN /thinkboxsetup/DeadlineClient-7.*-linux-x64-installer.run \
    --mode unattended \
    --unattendedmodeui minimal \ 
    --repositorydir /mnt/DeadlineRepository7 \ 
    --licenseserver @lic_thinkbox \ 
    --noguimode true \ 
    --restartstalled true 

WORKDIR /opt/Thinkbox/Deadline7/bin/