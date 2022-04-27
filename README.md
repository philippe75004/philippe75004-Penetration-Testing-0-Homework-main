## Week 16 Homework Submission File: Penetration Testing 1

#### Step 1: Google Dorking


- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is: Karl Fitzgerald

via a simple google search like this one: site:demo.testfire.net Chief Executive Officer

- How can this information be helpful to an attacker: we know he is also the chairman, we can now search for:

email addresses, usernames, paswords to gather informations (reconnaissance phase) via the OSINT framework: https://osintframework.com/


#### Step 2: DNS and Domain Discovery

Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results:

  1. Where is the company located: US, Sunnyvale, 94085 California

  2. What is the NetRange IP address: 65.61.137.64/26

  3. What is the company they use to store their infrastructure: Rackspace Cloud provider

  4. What is the IP address of the DNS server: 65.61.137.117, see below dns A record
  
demo.testfire.net	IN	A	65.61.137.117

#### Step 3: Shodan

- What open ports and running services did Shodan find: http ports: 80 + 443 + 8080

Web server running on Apache Tomcat/Coyote JSP engine1.1

#### Step 4: Recon-ng

- Install the Recon module `xssed`. 

marketplace install xssed

- Set the source to `demo.testfire.net`. 

module load xssed

- Run the module. 

options set SOURCE demo.testfire.net

Is Altoro Mutual vulnerable to XSS: yes as recon found 1 vulnerability on the search url which execute a script from a sec-r1z.com

See screenshots: RECON-NG-1 + RECON-NG-2 

### Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

- Command for Zenmap to run a service scan against the Metasploitable machine: nmap -sV 192.168.0.10
 
- Bonus command to output results into a new text file named `zenmapscan.txt`:

nmap -sV -oN /tmp/zenmapscan.txt 192.168.0.10

- Zenmap vulnerability script command: nmap -sV --script=vulscan/vulscan.nse demo.testfire.net

- Once you have identified this vulnerability, answer the following questions for your client: actually see screenshot, no findings but let's pretend XSS vulnerability:

  1. What is the vulnerability: XSS = Cross_Site Scripting

  2. Why is it dangerous: Attacker can remotely execute scripts and accessing not allowed data like databases, usernames, password...

  3. What mitigation strategies can you recommendations for the client to protect their server: Output Encoding and HTML Sanitization for example, the variables should not be interpreted as code instead of text;
  
 *References: https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html
  

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
