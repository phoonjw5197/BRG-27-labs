# BRG-27-labs
1.	Introduction

Over the course of the (Introduction to Server Environments and Architectures) lab, I embarked on a hands-on journey through the foundational concepts and practical skills essential for Linus administration and cloud computing. From setting up a Linux environment and navigating the command line, to configuring cloud instances and automating tasks with Bash scripts, each activity deepened my understanding of how real-world server environments operate.
This journal documents my progress, challenges, and key takeaways from each lab. It also reflects on how these experiences have shaped my technical confidence and prepared me for future roles in my next career.

2.	Linux Environment Setup and GitHub Integration
Lab: GitHub Setup - I signed up a new GitHub account from https://github.com and start a new repository. I explored GitHub portal environment and started to documenting the Lab progress in the new create BRG-27-labs repository with adding a README.md
https://github.com/phoonjw5197/BRG-27-labs
 



Lab: Linux Environment Setup – To preparation of this lab, I download the Ubuntu ISO from the https://ubuntu.com/download/desktop and download the virtual box from the https://www.virtualbox.org/ website.

 

I install VirtualBox and explore the application interface. I started to create new VM by add the machine name, mounting the Ubuntu ISO file from my PC path and choose the OS type.
 



Config the username – Add the user and password as per my VM login credential  

Configure VM resources settings - 4GB RAM, 1 CPU, 25GB disk space 


 


Once the resource has been confirmed, I click finish to powering up the VM and the Ubuntu VM is now running and installing the Ubuntu OS.

  

The Ubuntu VM is now running.

 




I trying on install VMware Workstation and try to installing Ubuntu VM with the same configure and I am able to to get the same result VM up and running.

 

Lab: Familiarity with Ubuntu Linux – Basic command line
I use the some of the Basic command line navigation to manage the file system. I use the 
pwd - to see where in the file system
ls - to list file and folder in the current directory
cd - to move into the Documents directory
mkdir - to create a new testlab folder
touch - to create a new empty testfile.txt in the testlab folder
cd.. - allow me to go up one level back to Documents folder
ls -l – to show the current long listing format (shows permission, size and date)
 
Understand directory structure /home
I use some of the command line navigation to access home directory, it is a personal directory for user
Cd ~ - To goes to home directory
pwd - to show me I in the home directory
ls - list the file in home directory
ls -a - to list the the files includes hidden files

 

Understand directory structure /var
I use some of the command line navigation to access var directory, it is a variable data file that changes during system operation.
cd /var - To go to var directory
pwd - to show me in the var directory
ls - list the file in var directory
cd log - to goes in log directory
ls -lh – To list the file with log format and human -readable file sizes

 

Understand directory structure /etc
I use some of the command line navigation to access etc directory, it is a configuration files for the system and installed software.
 
Understand man to explore Linux manual pages.
I try to use man mkdir to access the manual of using mkdir, it is showing the details of using this command of mkdir.
I learn that there is a mkdir -v verbose command to print message for each created directory
•	  
Reflection Linux Environment Setup

1.	What challenges did you encounter during the virtual machine setup?
- I faced challenges when setting up multiple VMs on my personal PC, as it caused the PC to slow down due to resource constraints. I realized that while VMs are powerful, they require reasonable resources to run smoothly.

2. What did you learn about virtualization tools and their differences?
- I experimented with Oracle VirtualBox and VMware, and both allowed me to set up VMs successfully. I found that both tools can achieve the same result.

3. How confident do you feel using Ubuntu after completing this lab? 
- I feel highly confident using Ubuntu, as I found it easy to find resources and guides online. The lab helped me become familiar with the operating system, and I'm comfortable navigating its interface.

4. In what ways can a virtualized Linux environment help in industry scenarios? 
 	- Virtualization enables easy deployment and scaling of applications, making it ideal for cloud computing and large-scale infrastructure.
3. Linux Services, Permissions, and Bash Scripting
Service Configuration and User Permissions
Linux Services configuration – I am using terminal to install and update multiple services Install Apache Web service, firewall (UFW) and SSH service
sudo apt update - refreshes the list of available packages and their versions.
sudo apt install apache2 - installs the apache HTTP server.
sudo systemctl status apache2 – to check the apache service status
sudo systemctl stop apache2 – to stops the web server.
sudo systemctl start apache2 – to starts the Apache2 service if it's not already running.
 
 
sudo nano /var/www/html/index.html – to make soeme change of Apache web page
 
Browe the localhost using browser to check if the apache web service running and the check if the index.html updated.
 
I try to use some command to enable firewall and add port 80 in the rule.
sudo ufw enable - to enable the firewall
sudo ufw status verbose – to check the current firewall status, I check before and after the enabling the firewall 
sudo ufw allow 80/tcp – add and allow port 80 inbound from anywhere 

 
sudo apt install openssh-server – install SSH program, show the ssh sever already install.
 









systemctl list-units --type=service – to shows all currently active services.
 

Add user - I adding the user using as following
sudo adduser sshuser – This will add a new sshuser and ask to setup a password
less /etc / passwd – This to check the user list and information, found sshuser add to the list.
 

 


Linux Permissions - I perform using this user permission lab to hands on Linux file permissions, user management and group-based access control.

Create users using command,
sudo adduser alice
sudo adduser bob
sudo adduser mallory
 

Create group and add users using command,
sudo groupadd sharedgroup
sudo usermod -aG sharedgroup alice
sudo usermod -aG sharedgroup bob

 

Create shared folder and files using command,
sudo mkdir /home/shared
cd /home/shared
sudo touch file{1..10}

 
 

Set Ownership and Permissions using command,
sudo chown -R root:sharedgroup /home/shared - ensures that only members of sharedgroup (e.g. Alice and Bob) have group-level access.
sudo chmod -R 750 /home/shared - 7 (rwx) → Owner (root) has full access, 5 (r-x) → Group (sharedgroup) can read and execute, but not write, 0 (---) → Others (e.g. Mallory) have no access.
sudo setfacl -m u:alice:rwx /home/shared - This gives Alice full access without changing the group permissions for Bob.
 

Test each user permission– using comman su – user

su - alice
cd /home/shared && touch testfile – alice has permission to write
 

su - bob
cd /home/shared && ls - bob has permission to read & execute         
touch testfile -   fails, due to no write permissionsu 
              




su - mallory
cd /home/shared  - fails, due to mallory is not in the sharedgroup

 

I use deluser to delete the no permission user,
sudo deluser mallory – key in admin password and user delete.
 















4. Total Cost of Ownership (TCO) Analysis
Printer Deployment 
DCP-J1050DW Inkjet Printer vs MFC-L8690CDW Laser Printer

I choose two model of printers from Brother, one Inkjet and one laser technology. 
DCP-J1050DW Inkjet Printer $208
MFC-L8690CDW Laser Printer $1018
Look at the unit price, I should a low-cost printer such as a budget inkjet than a more expensive laser printer, this is often the choice for home users. But let’s add some requirements and assumptions to analysis the total cost to verify which printer is more worth to purchase.
Period to consider: 5 years
Printing per week: 750 pages
Power on per week: 40 hours



Calculating cost
Knowing the number of consumables used over the time and the cost of each individual consumable, determine the cost for each type of consumable and then add these to determine the total cost of ownership.

Item Description	Type (Fixed/Variable)	Unit Price	Units Consumed (based on assumptions) 400 pages per week / 5yr / 40hr per week usage	Total Cost (Unit Price × Units Consumed)
DCP-J1050DW Inkjet Printer	Fixed	$208	 	 
 ink cartridge 200&200 pages (black/colour)	Variable	$70.50	260pcs	$18,330
Printing Cost 70.5/ 400pages	Variable	$0.18	104000 Pages	$18,720
Printing Power Usage 40hr per week	Variable	$0.28	135.2kw	$38.00
Cost for 5yr	 	 	 	$18,576
				
				
				
Item Description	Type (Fixed/Variable)	Unit Price	Units Consumed (based on assumptions) 400 pages per week / 5yr / 40hr per week usage	Total Cost (Unit Price × Units Consumed)
MFC-L8690CDW Laser Printer	Fixed	$1,018	 	 
Toner 3000&1800 pages (black/colour)	Variable	$441	22pcs	$9,702
Printing Cost 441/4800pages	Variable	$0.09	104000   pages	$9,547.20
Power Usage printing	Variable	$0.28	6032kw	$1,696.19
Cost for 5yr	 	 	 	$12,416.19




Summary 
When comparing the DCP-J1050DW Inkjet Printer and the MFC-L8690CDW Laser Printer, the inkjet's lower power usage is offset by the high cost of its ink cartridges ($70.50) and a higher per-page printing cost of $0.18. In contrast, the laser printer's higher power consumption is balanced by the cost-effectiveness of its toner ($441), which yields a lower per-page printing cost of $0.09 (based on 4800 pages per toner).
Over a 5-year period, assuming 400 pages printed per week (totalling 104,000 pages), the total printing costs would be:
- DCP-J1050DW Inkjet Printer: $18,576
- MFC-L8690CDW Laser Printer: 12416.19
Despite the laser printer's higher upfront cost, its lower per-page printing cost makes it the more economical choice in the long run, potentially saving $6,160 or more over 5 years compared to the inkjet printer ($18576 - $12416). Therefore, I would recommend the MFC-L8690CDW Laser Printer for its cost-effectiveness over time.
Reflection on this printer deployment
1. Based on the TCO, which printer has been the most cost-effective over 5 years?
The MFC-L8690CDW Laser Printer is the most cost-effective option over 5 years, with a total cost of $12,416 compared to the DCP-J1050DW Inkjet Printer's total cost of $18,576.
2. Would the answer change for a home user who prints only 5 pages per week? With just considering the printing cost and initial price
- DCP-J1050DW Inkjet Printer: 1,300 pages x $0.18 per page = $234 + $208 (initial cost) = $442
- MFC-L8690CDW Laser Printer: 1,300 pages x $0.09 per page = $117 + $1,018 (initial cost) = $1,135
In this case, the DCP-J1050DW Inkjet Printer would be the more cost-effective option for a home user who prints only 5 pages per week, with a total cost of $442 compared to the MFC-L8690CDW Laser Printer's total cost of $1,135.






5. Cloud Server, DNS Setup and SSL Configuration
Cloud Sever Setup
I signing up a Amazon Web Service (AWS) Free Tier:  https://aws.amazon.com/free
I start the lab, log into the Amazon EC2 management console choose Asia Pacific (Singapore zone)
Step to launch instance,
-	Add Server Name : Ubuntu VM Lab
-	Choose Ubuntu Server 24.04 OS Image 64bit (x86)
 
-	Add instance type with free tier with 1 vCPU, 1GB memory, 8GB storage
-	Create new key pair webserver-key.pem for use Open SSH connection later.
-	Create a security group with add rule allow SSH, HTTPS, HTTP, allow from anywhere being a public webserver
-	Click Launch Instance to start the instance
-	 
-	Check my running instance
-	 
-	I can connect using the AWS web console with public address
-	 
-	I try also using SSH client to connect my EC2 instance
 

-	Install Apache, I start Apache web service with sudo apt update and sudo apt install apache2 

-	Verify webserver and test 

o	sudo nano /var/www/html/index.html to edit my web page
o	verify my website with browse public ip 
 
 
Linking to files from my webserver
-	I downloaded the file from internet, and move it into the html directory, then create link in index.html
o	wget http://www.eecs.berkeley.edu/Pubs/TechRpts/2009/EECS-2009-28.pdf
o	sudo cp EECS-2009-28.pdf /var/www/html/
o	<a href="filename.pdf">Click here</a> -add this link into my index.html
 

-	Access my host website and the link is now added and able click to view the PDF. 
 
 
DNS Management
•	Domain used and DNS record configuration.
-	Obtaining a domain name at AWS route 53 – jwpbootup.com
o	Check the domain name availability and register the domain name
o	Proceed to check out payment $14 for 1 year domain name 


 
-	Linking my domain name to my web server public ip
o	Access to route 53 hosted zone add a A record route to my current public ip 13.215.248.255
o	Wait for a while, testing to access my website by using domain name - http://jwpbootup.com/

 

•	Tools used to verify DNS propagation.
I using command ping and nslookup to verify my DNS propagation progress.

 

SSL Certificate with Let’s Encrypt
•	Certbot usage and challenges.
Pre-requisites my host server ssh -i pemkey.pem ubuntu@[yourdomain-name-goes-here.com] and wget http://[yourdomain-name-goes-here.com]
 

Steps to Enable HTTPS Using Let’s Encrypt
-	sudo snap install core; sudo snap refresh core; sudo snap install --classic certbot
-	 
-	Run sudo certbot –apache to deploye the certificate for jwpbootup.com
-	 
-	Successfully deployed certificate for jwpbootup.com to /etc/apache2/sites-enabled/000-default-le-ssl.conf
-	Congratulations! I have successfully enabled HTTPS on https://jwpbootup.com
-	
 

Reflection on Cloud Server, DNS Setup and SSL Configuration
-	The benefits of cloud deployment over local virtualization in term of 
o	Scalability: Cloud instances can be scaled up or down instantly without hardware limitations.
o	Cost Efficiency: You pay only for what you use—no upfront hardware costs or maintenance.
o	Accessibility: Cloud servers are accessible from anywhere with internet access, ideal for remote work
-	DNS (Domain Name System) is the backbone of human-connection internet navigation. 
o	DNS help user to access website easily discover or accessible instead of memorize the IP address.
o	DNS propagation take time due to need to reach DNS Servers around the world.
-	TLS is important, without TLS (HTTPS), website is vulnerable to data can be intercepted, login forms and sentitive data are expose in plaintext.
Best practice on avoid unexpected cost: Stop or terminate unused instances and use automation to manage lifecycle and costs.
6. Bash Coding, Automation and Cron Jobs
Bash Code Lab - Start bash coding with Hello Bash World!
nano somecode.sh – to start coding 
 
Ctrl + O to Save and run script
chmod 777 somecode.sh – make script executable
./somecode.sh – execute the script 
I try to modify the echo to  "Welcome to the Bash scripting lab!"
 
 

Implementing Loops and Conditionals

#!/bin/bash

echo "System Information Script"

# Display current user
echo "Current User: $(whoami)"

# Loop through the next five numbers
for i in {1..5}
do
    echo "Iteration: $i"
    sleep 1s
done

# Conditional Statement
read -p "Enter a number between 1 and 10: " number

if ! [[ "$number" =~ ^[0-9]+$ ]]; then
    echo "Invalid input: Please enter a numeric value."
    continue
fi

if [ "$number" -le 5 ]; then
    echo "You entered a number less than or equal to 5."
elif [ "$number" -le 10 ]; then
    echo "You entered a number greater than 5 but less than or equal to 10."
else
    echo "Number out of range."
fi

Ctrl + O to Save and run script
chmod 777 system_info.sh – make script executable
./ system_info.sh – execute the script 
 
My Output with enter 8 in the range and enter 11 out of range:

 

Automating System Monitoring Tasks
#!/bin/bash

echo "System Resource Monitoring"

# Number of iterations
read -p "How many times would you like to monitor the system? " iterations

# Loop based on user input
for ((i=1; i<=iterations; i++))
do
    echo "----- Monitoring $i -----"
    
    # Display CPU usage
    echo "CPU Usage:"
    top -b -n1 | grep "Cpu(s)"

    # Display Memory usage
    echo "Memory Usage:"
    free -h

    # Display Disk usage
    echo "Disk Usage:"
    df -h | grep "^/dev"

    echo "-----------------------"
    sleep 5s
done

echo "Monitoring complete."

Ctrl + O to Save and run script
nano resource_monitor.sh
chmod 777 resource_monitor.sh – make script executable
./ resource_monitor.sh – execute the script 









My Output 3 times monitor the system:
 
Bash with variables 
a="Hello bash using variables"
echo $a
Ctrl + O to Save and run script
nano somevariables.sh
chmod 777 somevariables.sh– make script executable
./ somevariables.sh– execute the script  

a=10
 b=5
 c=$((a+b))
 echo $c
Ctrl + O to Save and run script
nano somevariables2.sh
chmod 777 somevariables2.sh– make script executable
./ somevariables2.sh– execute the script  

 
Reflection on this bash code lab
- This loop is useful for creating a timed sequence or countdown.
- The script checks the user’s input using a conditional statement, print out of range if invalid.
- The script already includes a regular expression check to ensure the input is numeric. If the input is not a number (e.g., letters or symbols), it prints: "Invalid input: Please enter a numeric value."
- The free -h command shows memory usage statistics in a human-readable format. 
- Automating system monitoring helps administrators by saving time, no need for manual checks ensuring consistency, regular, scheduled monitoring avoids human error.
- Understand that we can use assigned variables to perform output / calculation.




Creating the backup script
I will start to lab activity with create backup script, to start the lab activity, I create some folder as below:
touch file1
 touch file2
 touch file3
 touch file4
 touch file5
 mkdir testfolder
 cd testfolder
 touch file11
 touch file22
 touch file33
 touch file44
 touch file55
 
Write the backup script,
#!/bin/bash
mkdir -p /home/adminjw/backup
cp -r /home/adminjw/Documents/* /home/adminjw/backup/
 

1.	./testscript.sh – to execute the backup script, check the document folder, the backup folder and files copy completed.
2.	I making the script available system wide using command to move the backup script to /usr/bin and change the owner, now I can run the file globally.
     sudo mv /home/adminjw/testscript.sh /usr/bin/testscript.sh
     sudo chown adminjw /usr/bin/testscript.sh
 
 

3.	Enhance my backup script with zip up all of the files and provide a date as the filename. With using command,
Get the current date
now=$(date +"%d_%m_%y") - Get the current date
zip -r /home/adminjw/backup/backup_$now.zip /home/adminjw/backup/ - Create a zip archive of the backup directory (recursive flag added)
 
Schedule automated backup tasks using cron jobs.
4.	Enhance my backup script ensure the backup script is running in 2 minutes at every hour. With command,
sudo nano /etc/crontab
   2 * *   *   *   adminjw /usr/bin/testscript.sh

 

7. Consulting Simulation
•	Overview of your proposed solution (stack, budget, security).
I am simulating a scenario while consulting for new webserver on premise vs on cloud.

I proposed the solution with two configurations and provide the information to the peer to consider.
-	On premise Web Server: 
o	Apache2 on Ubuntu Server 22.04 LTS
o	Database: MySQL for structured data storage
o	Backend Scripting: PHP for dynamic content generation for website service
o	Automation: Bash scripts for backups, log rotation, and service monitoring
-	Budget 
o	Initial hardware investment: Moderate (I might have repurposed existing server)
o	Ongoing costs: Low (no recurring cloud fees)
o	Maintenance: requires in-house expertise and time

-	Security Implementation
o	Full control over physical and network security
o	Configured UFW firewall, SSH hardening, and TLS via Let's Encrypt
o	ACLs and file permissions tightly managed

-	On Cloud Web Server: (Same LAMP stack deployed on a cloud VM (e.g., AWS EC2 or Alibaba Cloud))
o	Apache2 on Ubuntu Server 22.04 LTS
o	Database: MySQL for structured data storage
o	Backend Scripting: PHP for dynamic content generation for website service
o	Cloud-native tools for monitoring, scaling, and backups

-	Budget 
o	 Pay-as-you-go pricing: Predictable monthly costs
o	No upfront hardware investment
o	Potentially higher long-term cost depending on usage 
o	No in-house expertise require

-	Security Implementation
o	- Built-in DDoS protection and managed firewalls
o	- Encrypted storage and traffic
o	- Shared responsibility model—provider handles infrastructure, user handles OS and app security

-	From the short details information provided above, I gather the feedback summary from peers from different area,
o	Scalability & High Availability
Peers noted the on-premises setup lacks auto-scaling and single-point-of-failure risk in both models.
o	Backup Redundancy
Recommendation to implement off-site/geodiversity backups beyond simple local scripts.
o	Compliance & Data Residency
Emphasis on data sovereignty requirements and encryption at rest/in transit for both on-prem and cloud.
o	Cost Projection
Ask for a detailed 3-year TCO comparison, including energy, staffing, and reserved-instance options.

-	From the feedback details information provided above, I incorporate the suggest summary to peers from each area,

o	Auto-Scaling & HA
Introduced containerization with Docker Compose (on-prem) and AWS Auto Scaling Groups (cloud), plus HAProxy load balancing.
o	Geodiverse Backups
Extended backup script to push snapshots to an off-site S3 bucket in a separate region and configured lifecycle policies.
o	Compliance Measures
Mapped data flows to ensure residency controls, enforced full-disk encryption on on-prem disks, and enabled customer-managed keys (CMKs) for cloud storage.
o	3-Year TCO Model
Created a side-by-side financial projection covering hardware depreciation, power/cooling, staff hours, reserved instances, and cloud egress fees

I strengthened the proposal by providing more detailed information on scalability, cost estimation, and security measures for both solutions, making it easier to make an informed decision.

8. Industry Relevance and Final Reflection
8.1). From these lab series relate to career position on - System Administrator (Sysadmin) or Cloud Infrastructure Engineer. Ability to Installing and configuring Linux servers, managing services, and handling permissions are core Sysadmin tasks. Working with IaaS platforms like AWS EC2 and Azure, managing cloud costs, and deploying scalable services are essential skills.
8.2). This experience significantly boosted my confidence in handling real-world server environments by providing hands-on exposure to both physical and virtualized Linux environments. This lab also teaches me how to deploy and manage cloud infrastructure using AWS and other cloud platforms. Reinforcing the importance of automation through Bash scripting for tasks like backups and monitoring. Helping me understand cost management and the total cost of ownership (TCO) in IT decision-making.



8.3). Skills I get confident and improved in
•	Linux System Administration: Service management, file permissions, and scripting.
•	Cloud Computing: Deploying and managing virtual machines on AWS and other cloud platform.
•	Bash Scripting: Automating tasks like backups permission, and server service functions.
•	Networking Fundamentals: DNS configuration and understanding digital certificates.
•	Cost Analysis: Using TCO to compare infrastructure options.

This unit offered a comprehensive and practical overview of server environments, making it an excellent resource for those looking to break into the field.
