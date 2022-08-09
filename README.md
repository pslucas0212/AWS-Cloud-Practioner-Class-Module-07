# Monitoring and Analytics


[AWS Cloud Practitioner Home](https://github.com/pslucas0212/AWS-Cloud-Practioner)

### Introduction

Use metrics to measure how well systems and process are running.  

Monitoring is observing systems, collection metrics and use the metrics to make changes.

Alerting to send you messages when things don't go correctly

#### Transcript
As the owner of the coffee shop, I want to watch what's going on throughout the day, making sure things are running smoothly. In the coffee shop, I can see people are getting their coffees, and things look generally fine. But I can't just sit there and watch things all day long. I would like to eventually leave and maybe come back at the end of the day, and be able to check in and see how the shop did when I was gone. 


For example, I might want to know how many coffees were sold today? How long was the average wait time for someone when ordering a coffee? Did we run out of inventory for anything today? Even better yet, I'd love to be able to be automatically alerted if the wait times become too long. That way I can call in another employee or go pitch in myself. Every business, including this coffee shop, can use metrics to measure how well systems and processes are running. 


This idea of observing systems, collecting metrics, evaluating those metrics over time, and then using them to make decisions or take actions, is what we call monitoring. 


It's important to set up monitoring in the cloud. With the elastic nature of AWS services that dynamically scale up and down, you'll want to keep a close pulse on your AWS resources to ensure that your systems are running as expected. 


For example, if an EC2 instance is being over-utilized, you can trigger a scaling event that automatically would launch another EC2 instance. Or if an application starts sending error responses at an unusually high rate, you can alert an employee to go take a look at what's going on. 


In the next few videos, we will cover a variety of tools that help you monitor your AWS environment. This monitoring will help you measure how your systems are performing, alert you when things aren't right, and even help you debug and troubleshoot issues as they come along.

### Amazon CloudWatch

You need visibility in to your system and its performance.  

Amazon CloudWatch allows you to monitor your AWS infrastructure and the applications running in AWS.  Create custom metrics to provide alerts.  To do this you create a CloudWatch alarm and you can recieve an alert based on this metric.  You can send message (SMS) to alert you.

Amazon Cloudwatch dashboard to show you metrics from all your systems.  

- Access to all metrics from a central locations.  Data on all AWS services and your applications
- Visibiltiy across applications, infrastructre and services. 
- Reduce MTTR (mean time to resolution) and TCO

Drive insights to optimize applicaitons and operational resources.

#### Transcript
Now we're making lots of coffee, serving customers and everything seems to be going spiffy in our coffee shop. But as we run espresso machines more and more, use mugs, constantly open and close the fridge, we want to be able to make sure we're alerted to something which might have gone awry. Maybe an espresso machine needs to be cleaned or repaired. The point is, as a business owner, you need visibility into the state of your systems. Are things running well? Do you see a degraded customer experience? Are you frequently delivering the wrong drink to customers or is everyone getting their orders as expected. You have all sorts of questions about the success of your operations. 


And the same idea applies to systems built on AWS. You need a way to monitor the health and operations of your solutions. Luckily, you don't need to build out your own monitoring platform. We have done this for you. 


Introducing Amazon CloudWatch. CloudWatch allows you to monitor your AWS infrastructure and the applications you run on AWS in real time. It works by tracking and monitoring metrics. Think of metrics as variables that are tied to your resources. For example, the amount of espressos made by an espresso machine or the CPU utilization of an EC2 instance. 


Let's take a customer approach for our coffee shop. Say we have an espresso machine and it needs to be cleaned after it makes 100 espressos. CloudWatch allows us to create a custom metric called Espresso Count. And once it hits 100, we want to alert staff to clean the machine. Simple, right? Well with CloudWatch, you can accomplish this by creating what is called a CloudWatch alarm. You set a threshold for a metric, and when that threshold is reached CloudWatch can generate an alert and trigger an action. This means we can alert on the custom metric, in this case, hitting 100, and then perform an action. 


Even better, CloudWatch alarms are integrated with SNS. So we can then send an SMS to the manager to say, clean the machine. You can create all sorts of custom alarms for metrics from all different types of AWS resources. 


Now, what if we want to aggregate all those metrics in a single pane of glass? Well, we can use CloudWatch's dashboard feature. Think of a dashboard as a screen, which lists out metrics in near real time. In our case, we can create a CloudWatch dashboard which will show us all our espresso machines and their espresso counts so we can proactively monitor them. These dashboards would auto refresh when they are open so we can see an up-to-date view of our resources. 


Finally, what are the benefits of using a service such as CloudWatch? Well, the first one is that you can have access to all your metrics from a central location. This enables you to collect metrics and logs from all your AWS resources applications, and services that run on AWS and on-premises servers, helping you break down silos so that you can easily gain system-wide visibility. 


You can also get visibility across your applications, infrastructure, and services, which means you gain insights across your distributed stack so you can correlate and visualize metrics and logs to quickly pinpoint and resolve issues. This in turn means you can reduce mean time to resolution, or MTTR, and improve total cost of ownership, or TCO. So in our coffee shop, if the MTTR of cleaning hours restaurant machines is shorter then we can save on TCO with them. This means freeing up important resources like developers to focus on adding business value. 


Lastly, you can drive insights to optimize applications and operational resources. By, for example, aggregating usage across an entire fleet of EC2 instances to derive operational and utilization insights. And now our staff can focus on serving coffee versus constantly cleaning machines before they are due to be cleaned. 


And there you have it, folks - you're up to speed on what CloudWatch entails. Now if you excuse me, I have a date with an espresso machine to refill my coffee.

### AWS CloudTrail

AWS CLoudTrail a comprehensive API auditing tool.  Every request gets logged in the CloudTrail system - user, IP address, response,time of the call...
- Identity of API caller
- Time of API call
- Source API of the caller
- more

CloudTrail logs can be saved in S3 buckets and made immutable

CloudTrail INsights automaticaly detects unsual API activities on an AWS account

#### Transcript
The Cash Register, one of the world's first self-auditing devices. The principle is simple: trust but verify. You have your entire store being run by a clerk that you trust, but you want to make sure that the cash in the drawer matches the actual sales. So every transaction then is recorded and tabulated. So at the end of the day, you know exactly what should be there. 


Being able to audit transactions in IT is a critical element in most compliance structures. But in a physical data center, there are so many places where a human can, even by accident, make changes without any record of that change getting recorded. At AWS, that problem goes away because everything is programmatic. 


Introducing AWS CloudTrail, the comprehensive API auditing tool. The engine is simple, every request made to AWS, it doesn't matter if it's to launch an EC2 instance, or add a row to a DynamoDB table, or change a user's permissions. Every request gets logged in the CloudTrail engine. The engine records exactly who made the request, which operator, when did they send the API call? Where were they? What was their IP address? And what was the response? Did something change? And what is the new state? Was the request denied? 


From an auditing perspective, well, this is fabulous. So imagine that you're dealing with an auditor who is checking to make sure that nobody from the outside can access your database. That's a good thing. Well, okay, you build a security group that locks out external traffic. But remember that a root-level administrator still has permissions to change those settings, right? 

Well, so how do you prove to the auditor that the security group settings never changed? The answer is CloudTrail. And then CloudTrail can save those logs indefinitely in secure S3 buckets. In addition, with tamper-proof methods like Vault Lock, you then can show absolute provenance of all of these critical security audit logs.


### AWS Trusted Advisor

AWS Trusted Advisor is an automated advisor that evaluates against five pillars
- Cost optimization
- Performance
- Security
- Fault Tolerance
- Service Limits

Some capabilites are free and some are for charge


Examples. MFA not turned on for root.  S3 buckets not being used (under utilized).  Systems not backedup.

TA can be set up to send out email alerts

#### Transcript
When running a business, you might need some advisers who can come in from the outside and say, hey, this process should be streamlined. Or, hey, I have some good tips on how to save money on your overhead. Or even, hey, I noticed I was able to waltz right in, go behind your cash register, and open the drawer without anyone noticing. Not good. 


The point I'm trying to make is, sometimes it's nice to have someone who knows the industry best practices, and knows what to look for, come in, and tell you what you need to change in order to run more efficiently, be more secure, or to save some money.

 

AWS has an automated advisor called AWS Trusted Advisor. This is a service that you can use in your AWS account that will evaluate your resources against five pillars. The pillars are cost optimization, performance, security, fault tolerance, and service limits. Trusted Advisor in real time runs through a series of checks for each pillar in your account, based on AWS best practices, and it compiles categorized items for you to look into, and you can view them directly in the AWS console. 


Some checks are free and are included in your AWS account, and others are available depending on the level of your support plan. Some examples of checks are, if you don't have multi-factor authentication turned on for your root user, it's going to let you know. If you have underutilized EC2 instances that might be able to be turned off in order to save money, or if you have EBS volumes that haven't been backed up in a reasonable amount of time, it will let you know that, too. To get a better idea, let's look at AWS Trusted Advisor in my own account. 


I'm already logged into the console, and I'm going to type in Trusted Advisor into the search. This brings me to the Trusted Advisor dashboard and I'm going to click on the Cost Optimization pillar first to view what it has found. You can see right away there are three levels of items it is showing me. There was the red circle, which means action recommended. The orange triangle, which means investigation recommended. And the green square, which means that there were no problems detected. 


Lucky for me, I don't have any red items for Cost Optimization, but I do have some orange items. Under Cost Optimization checks, I can read more about each check that Trusted Advisor ran. In this account, I do have some RDS instances that are idle, as well as some underutilized EC2 instances and EBS volumes. I could decide to scale these instances down vertically to save on cost, or if they aren't being used at all I could decide to delete those instances and those EBS volumes altogether. It would require some investigation for me to determine what to do here. 


Now, let's click on the Performance pillar. On this one, I don't have any warnings, but we can still read what checks Trusted Advisor performed. Like this one, for example, which checks for EBS volumes whose performance might've been affected by the throughput capability of the EC2 instance that it's attached to. 


Next, let's select the security pillar. In this demo account, you can see there are four alerts that are at the action recommended level. Trusted Advisor is trying to alert me, telling me I have weak password policies for IAM users, multi-factor authentication is not turned on for the root user, and there are security groups allowing public access to EC2 instances. All of these items are putting the resources in this account at risk, and should be dealt with as soon as possible. 


Now let's move on to fault tolerance. For this, there were a few things that are found to be insufficient. First, Trusted Advisor is telling me that there are EBS volumes without snapshots in this account. Remember, a snapshot is a backup. So without backups, if I had an EBS volume fail, I would lose that data. 


Another alert we have here is that my EC2 AZ balance is at the action recommended level. This means that my EC2 instances are not properly launched across AZs. So if one AZ has trouble, my application might incur an outage. Deploying across AZs would be the answer to this one.

 

Finally, let's check out Service Limits. This pillar will tell you when you are approaching or hitting AWS service limits. A lot of service limits are soft limits, meaning they are restrictions that can be lifted to some degree. It's good to know when you are approaching one of those limits, and when it's time to turn in a Support ticket with AWS to get them changed. In this account, I can see that I have five VPCs, which is the regional limit. So I've hit that specific service limit. 


Trusted Advisor can help point you in the right direction when it comes to the five pillars. You can set up email alerts that go out to billing, operations, and security contacts, as checks get run in your account. Make sure you have Trusted Advisor turned on so that you too can start taking action to optimize your AWS account.

### Summary

AWS CloudWatch - system analysis
AWS CloudTrail - audit trails
AWS Trused Advisor - advise on "optimizing" services

#### Transcript
Understanding what is happening in your environment is key to maintaining efficient, secure, and compliant applications. 


We discussed how CloudWatch can provide near real-time understanding of how your system is behaving, including being alerted to conditions that require your attention. CloudWatch also gives you the ability to look at those metrics over time as you tune your system for maximum performance. 


We discussed how CloudTrail can help you know exactly who did what, when, and from where. It answers all of your AWS auditing questions, except why they did it. 


And finally, we looked at Trusted Advisor that compiles a quick dashboard of over 40 common concerns around cost, performance, security, and resilience in an actionable dashboard. 


There are, of course, many additional monitoring and analytical tools available for your use, but this will help you get a good feeling for some of the variety AWS offers your business.
