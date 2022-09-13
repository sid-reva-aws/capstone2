# capstone2

**covid-19 project**
---------------------------------------------------------------------------------------------------------
  Deploying a covid-19 website on AWS S3 This section describes how to deploy the angular application and host them in the AWS S3 service.

  Deploy Angular app to AWS S3 service: Let’s deploy our angular application to serverless S3 service. In order to continue, you will need an AWS account. You can  create a free account on https://aws.amazon.com/console/.

  Create S3 bucket to deploy website Once you have successfully created an account and logged in, you can navigate to S3 under services -> storage option. The first step is to create an S3 bucket name. The bucket name is unique across all AWS account and hence the generic name should not be chosen as it may be possibly taken.

  Also, you need to choose the bucket name wisely as S3 exposes the URL in the following format [BUCKET-NAME].s3-website.[BUCKET-ZONE].amazonaws.com

  Following the bucket name, you need to select the region. It makes sense to select the region closer to the user’s location which will provide faster application performance to the users.
  
Let’s click on the Create button to finally create our S3 bucket. Once the bucket is successfully created, you can find it under the S3 bucket list.

Click on the newly created bucket and then click on the properties tab.

Click on the “Static website hosting” card to define the entry page and error page for our application.

You will see three options there, you need to select “Use this bucket to host a website”. Here, you need to define the index and error document. In our case, we will define both the document as an index.html page.

Also, you can see the endpoint URL which will launch the application in the browser.

Let’s click Save and hit the browser with the given endpoint URL. At this stage, we are getting the following 403 forbidden errors. The reason is all S3 bucket policies by default are private which will make the application inaccessible to all the users.

We can manage the bucket policy under the “Bucket Policy” tab and grant the public access to all the users.

First, let’s go to the Permissions tab and click on the Edit button. Here, the following two options “Block public access through new public bucket” and “Block public and cross-account access through new public bucket” are set to true by default. Let’s uncheck them and click Save.

Next, you need to apply a policy that will grant anonymous users to access our data. We can copy the following policy and paste it under the Manage bucket policy section. You need to change the bucket name with your current existing bucket in the Resource property of the JSON object. 11.Also, it’s very important to only grant GetObject to the users and not PUT, DELETE, etc any kind of Edit access in order to prevent any security issues.

Deploy the Angular build Now let’s copy the angular build output (unzip dist.rar and copy the whole folder contents) that we discussed initially in the article generated at the dist path and upload it in S3. Once the files are successfully uploaded, you can navigate to the S3 endpoint URL and verify the application is up and running.


**s3-config-check project**
---------------------------------------------------------------------------------------------------------------
This python script checks the configuration on the deployed S3 buckets for MFA delete and Versioning. Configure your AWS user credentials having access to the S3 buckets using AWS configure command. Run the python script and an excel sheet will be created on same folder location with bucket config details like MFA delete, S3 versioning and recommendations.


**ec2-wordpress project**
---------------------------------------------------------------------------------------------------------------
Deploying a WordPress website on AWS EC2: This link provides information on how EC2 and RDS configuration is done on wp-config file once wordpress code is downloaded and extracted on EC2. The sample snapshots can be reviewed on below link: https://www.linkedin.com/pulse/integration-aws-ec2-wordpress-using-rds-pratik-kohad

The rar file contains the WP application config files and wp-config file updated with AWS sample RDS details which can be changed to the deployed RDS details.

Step 1 - First, we need to launch an ec2 instance on AWS. Step 2: we need to configure Apache WebServer.

login to the EC2 instance.
yum install httpd -y
Step 3 - Now install MYSQL.

Step 4 - Now install php7.2 (amazon-linux-extras install php7.2 ).

Step 5 - Now Download WordPress. wget https://wordpress.org/latest.tar.gz

Step 6 - Now Extract the package. tar -xvzf latest.tar.gz -C /var/www/html/

Step 7 - Setting up the /etc/httpd/conf/ httpd.conf file Making AllowOverride None to AllowOverride All

Step 8 - Setting Up the Amazon RDS instance. Setting Up name and password for the instance to access.

Step 9 - Now connect to the database using following command. mysql -h -u admin -p

Step 10 - Starting Httpd using CLI.

Step 11 - Use the following command to open WordPress. /wordpress after clicking on let's go it will direct you to the below page. After clicking on submit you will be directed towards contents to be copied to wp-config.php file. Copy the content from here and paste it into the wp-config.php file.

Step 12 - Copying content from WordPress to wp-config.php file. cat > /var/www/html/wordpress/wp-config.php cat /var/www/html/wordpress/wp-config.php Now click on Run the installation. You will be directed to the below page where you will be allowed to put the name and password.

Step 13 - Click on Install WordPress and then you will be directed towards the below page.

Step 14 - Now log in using credentials entered before. So our WordPress Application is Successfully Deployed.
