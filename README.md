# Shell Script to install jenkins

![Screenshot from 2024-11-28 23-11-04](https://github.com/user-attachments/assets/56da964c-8f95-4fc0-b475-92509c6bb23b)

This Bash script automates the installation of Java 17 and Jenkins based on the operating system (Debian-based Linux or macOS). The script defines three functions:

os(): Detects the operating system. If the script runs on Linux with apt package manager, it sets the os variable to "debian." If it runs on macOS, the variable is set to "mac." Unsupported systems trigger an error message and exit the script.

java(): Installs Java 17. For Debian, it uses apt to update repositories and install openjdk-17-jdk. For macOS, it installs openjdk@17 via Homebrew. The function prints messages indicating progress.

jenkins(): Installs Jenkins. For Debian, it configures Jenkins' official repository, updates, and installs Jenkins using apt. On macOS, it installs Jenkins LTS with Homebrew. Messages indicate status.

The script calls these functions in sequence to detect the OS and install the necessary tools, ensuring compatibility and automation.

# Setup Master-slave architecture
![Screenshot from 2024-11-28 23-17-06](https://github.com/user-attachments/assets/fb10a99d-da05-416e-9a6e-04dbf791480e)
Creating a node in order to setup master slave architecture, this is done by using private key, username and host information from a different system.

![Screenshot from 2024-11-28 23-17-46](https://github.com/user-attachments/assets/02faa159-94ef-4997-bcee-bf951673ea01)
this is made in order to run 5 different tasks, whatever are required from the user as per their demand.


# Setup Role based authorization


![image](https://github.com/user-attachments/assets/853d0507-e31c-4d44-87ad-c20310c77a16)

create a user according to the need, i will create one with the name of cats


![Screenshot from 2024-11-28 22-46-34](https://github.com/user-attachments/assets/a23cd621-8804-4cef-a2cd-6bae29b0c20f)

Create a role named PROJECT_ROLE, and give it read permission in the overall section.


![Screenshot from 2024-11-28 22-46-44](https://github.com/user-attachments/assets/03b1f373-6ff5-4888-8511-1ff9594a8033)

create a item role named project_meow with the pattern sense of "meow.*" , from the job section give it the permission of build, configure, read and workspace.


![Screenshot from 2024-11-28 22-47-04](https://github.com/user-attachments/assets/c344d4ab-d608-4972-ac7b-b9a201513d98)

create a globale role named cats and give it permisson of PROJECT_ROLE


![Screenshot from 2024-11-28 22-47-13](https://github.com/user-attachments/assets/2e8b33d3-33a3-4411-a750-b27589ce283b)

from item roles, give it the permission of project_meow which we created before.



![Screenshot from 2024-11-28 22-47-42](https://github.com/user-attachments/assets/9dbbf4ae-0eed-40c0-b216-b1176c6bd588)

now login from the cat user which we created before.


![Screenshot from 2024-11-28 22-47-58](https://github.com/user-attachments/assets/b9fa07eb-2632-4301-8dc9-cd510cb8d58d)

we will see the projects with the same pattern which we referred to in the item roles section.

# Create a pipeline to execute a shell script, on git, on scripting task, Monitor disk utlization and send mail if > 80%, Process Management, take inputs, check for errors, cleanup, backup, logging

![Screenshot from 2024-11-28 23-21-52](https://github.com/user-attachments/assets/dd48667f-5446-4343-ac99-9438e4311e93)

All the scripts in order to run the pipeline are present on the github, namely JenkinsFile, meow.sh, script1.sh and script2.sh

![image](https://github.com/user-attachments/assets/2e997529-b6d1-444e-817b-d04342f79db8)

This Jenkins pipeline automates tasks with three stages: Git Checkout (cloning a repository), Check Disk Usage (running script1.sh), and Process Management (running meow.sh). Triggered hourly, it sends an email notification on failure, providing job details and console output link to the specified email address.

![Screenshot from 2024-11-28 23-25-32](https://github.com/user-attachments/assets/3b6d9553-75cc-4078-ac4c-fa5739331190)

This Bash script identifies resource-intensive processes. It lists the top 5 processes consuming the most CPU and memory using `ps aux` with appropriate sorting. Additionally, it detects zombie processes (stuck processes) by filtering for processes with a `Z` state using `awk`, ensuring efficient process monitoring and troubleshooting.

![image](https://github.com/user-attachments/assets/9bd27dd7-433a-4ab8-b055-120e16269423)

This Bash script monitors disk usage of the root directory. It retrieves the usage percentage and checks if it exceeds 80%. If so, it prints a warning and exits with an error code. Otherwise, it confirms normal usage. This helps prevent disk space issues by alerting administrators proactively.

![Screenshot from 2024-11-28 23-28-31](https://github.com/user-attachments/assets/2783c6d8-b68b-4b60-8ae5-f99963112699)


This Bash script automates backup creation with options for compression. It accepts source and destination directories via command-line arguments, validates them, and ensures the directories exist (creating the destination if necessary). Backups are named with timestamps for uniqueness. If the `-c` flag is provided, the backup is compressed into a `.tar.gz` file; otherwise, files are copied directly. Operations are logged in a file, and detailed error handling ensures reliability. Additionally, backups older than 7 days are automatically deleted to save space. This script streamlines backup management, combining flexibility, automation, and maintenance to safeguard critical data effectively.
