README

DATE: 171031 (YYMMDD)
AUTHOR: Robert Booth

PURPOSE:
This vagrant file was created to deploy a very basic Windows box and install the SaltStack minion on it for further configuration.

NOTE:
This file requires some leg work first to get the base image in the correct state for this to work. Follow the steps below.
c
WARNING:
It is my assumption that you will modify the sensitive information like passwords and firewall on the deployed box immediatly after deployment with SaltStack.


CREATED/TESTED ON:
Vagrant 2.0.0
Virtual Box 5.1.30
Windows 10



PREP WORK:

1. Create Virtualbox VM for Windows
   name: windows10base

2. Install Windows OS
  NOTE: Select "Domain join instead" for account

3. Username: ykdemo1
   Password: ykdemo

4. Run all system updates

5. Install Virtualbox Guest Additions.

6. Disable all firewalls (Domain, Private, Public)
The firewall should be configured once SaltStack runs

7. Run powershell as Administrator

8. Configure basic winrm setting. (Make sure completes without error. Needs to be private or domain network)
   winrm quickconfig

9. Shutdown Windows box

10. Create package for Virtualbox
   vagrant package --base windows10base --output windows10

11. Load box into library
   vagrant box add .\windows10 --name ykwindows10v1


----- YOU NOW HAVE THE IMAGE READY FOR VAGRANT -------

Update the config.yaml with your information and execute 
vagrant -otp="cccc.....ccccc" up

