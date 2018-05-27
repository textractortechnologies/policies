# 1. Introduction

Textractor Technologies LLC ("Textractor Technologies") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. As a provider of compliant, assisted chart abstraction and clinical note exploration software used by healthcare enterprises, Textractor strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by Textractor to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Textractor Customers.

Textractor provides secure and compliant cloud-based software. This hosted software falls into two broad categories: 1) **Platform as a Service (PaaS)** and 2) **Platform Add-ons**. These Categories are cited throughout polices as Customers in each category inherit different policies, procedures, and obligations from Textractor.

## 1.1 Textractor Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web Services](https://aws.amazon.com/) (AWS) by Textractor's cloud partner [Healthcare Blocks](https://www.healthcareblocks.com/) "AWS/Healthcare Blocks".

The network components and supporting network infrastructure are contained within the AWS and managed by AWS.  Textractor does not have physical access into the network components. <issue1>The Textractor environment consists of Cisco firewalls; nginx web servers; Java, Python, and Go application servers; Percona and PostgreSQL database servers; Logstash logging servers; Linux Ubuntu monitoring servers; Windows Server virtual machines; Chef and Salt configuration management servers; OSSEC IDS services; Docker containers; and developer tool servers running on Linux Ubuntu.</issue1>

Within the Textractor Platform on AWS/Healthcare Blocks, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Textractor assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

It is the responsibility of the Textractor to restrict, secure, and assure the privacy of all ePHI data at the Application Level.

* Within AWS/Healthcare Blocks, hosted load balancers segment data across dedicated Virtual Private Clouds for Textractor Customers.

<issue1>
The segmentation strategies employed by Textractor effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each Textractor Customer.

Additionally, IPtables is used on each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Textractor has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Textractor network and can only be accessed through a bastion host over a VPN connection. Access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business-justified reason. Remote access to internal servers is not accessible except through load balancers.
</issue1>

All Textractor applications and operating systems are tested end-to-end for usability, security and impact prior to deployment to production.

## 1.2 Version Control

Refer to the GitHub repository at [https://github.com/textractortechnologies/policies/](https://github.com/textractortechnologies/policies/) for the full version history of these policies.
