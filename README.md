# AWS: Cloud Servers

**OVERVIEW:** Deploy a Node.js server to AWS EC2

## Feature Tasks

Deploy a simple Node.js server to EC2 using Elastic Beanstalk:

-   Choose a server you’ve built previously:
    -   Option 1: A simple API or Web Server
    -   Option 2: A socket.io event Hub
-   The server **should** not require a database
-   Check in your server to GitHub

**Task 1:**

-   Create a new environment, using Elastic Beanstalk from the AWS Control Panel (GUI)
-   Manually deploy your application to this environment by uploading a .zip file

**Task 2:**

-   Using the same server, create a new environment using Elastic Beanstalk from your terminal
-   Manually deploy your application to this environment by using `eb deploy`

## Deployed Server Links

-   GUI deploy: http://elasticbeanstalk-env.eba-tzcaitau.us-west-2.elasticbeanstalk.com/
-   CLI deploy: http://class16ebclienv.eba-2rbpqm27.us-west-2.elasticbeanstalk.com/

## Process

-   **Add a User (IAM Management Console)**

    -   Click on “Add Users” (Access management ⇒ Users ⇒ Add Users)
    -   Enter User name, check “Access key - Programmatic Access”
    -   Click “Next: Permissions”
    -   Select “Add user to group”
    -   Click “Create Group”
    -   Use same group name
    -   Add “AdministratorAccess-AWSElasticBeanstalk”
    -   Click “Next: Tags”
    -   Click “Next: Review”
    -   Click “Create User”
    -   \*\*\*KEEP ACCESS KEY ID AND SECRET ACCESS KEY

-   **Provision the Environment (Elastic Beanstalk Management Console)**

    -   Click on “Create Application”:
    -   Application Name
    -   Tags (skip)
    -   Platform (Node.js, use defaults)
    -   Application Code (Upload your code)
    -   Source code origin (local file ⇒ .zip the files for your server; DO NOT INCLUDE NODE MODULES)
    -   Click “Create application”

-   **Create the AWS Elastic Beanstalk CLI (Terminal)**
    -   Type “aws configure”
        -   Enter Access Key ID (from Add a User above)
        -   Enter Secret Access Key
        -   Default region name - (us-west-2 if not already defaulted)
        -   Default output format - hit ‘enter’
    -   Type “eb init”
    -   Select a default region - **3**
    -   Select an application to use - **2** to Create a New Application
    -   Enter Application Name - **<new name>**
    -   It appears you are using Node.js. Is this correct? **y**
    -   Select a platform branch:
        -   **Node.js 14 running on 64bit Amazon Linux 2**
        -   Node.js 12 running on 64bit Amazon Linux 2
        -   Node.js 10 running on 64bit Amazon Linux 2 (Deprecated)
        -   Node.js running on 64bit Amazon Linux (Deprecated)
    -   Cannot setup CodeCommit because there is no Source Control setup, continuing with initialization. Do you want to set up SSH for your instances? **N**
    -   (In AWS Elastic Beanstalk, check “Applications” to see if your Application Name (in step 5 above) is listed.)
    -   In terminal, type “eb create <name>” (class16ebclienv) to create your environment _(this creates storage for the data - this will take some time)_
