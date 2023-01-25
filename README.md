<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.io/oC2aGZr_d.webp?maxwidth=640&shape=thumb&fidelity=medium" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create two virtual machines, Domain Controller and Client-1. Set Domain Controller IP to static. This enables the Client-1 to receive Active Directory services and permission to join Domain. Check connectivity between Domain Controller and Client-1 by enabling all ICMPv4 traffic in the local windows firewall of the Domain Controller and utilizing Command prompt in Client-1 and ping -t 10.3.0.4. 
</p>
<br />

<p>
<img src="https://i.imgur.io/HXvaJgU_d.webp?maxwidth=640&shape=thumb&fidelity=medium" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Active Directory Users & Computers. Next, promote the Virtual Machines to Domain Controller and enable all Active Domain Services. Create a new forest, "mydomain.com," and reboot the computer. Log into Domain Controller with the username "mydomain.com//labuser."
</p>
<br />

<p>
<img src="https://i.imgur.io/yohm1zt_d.webp?maxwidth=640&shape=thumb&fidelity=medium" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create two Orgazational Units named _EMPLOYEES and _ADMIN by right clicking on the domain area = New = Organizational Unit and complete the application. Select New and select user and fill out the information for the new user. In this case, let's use Jane Doe as an example. She is the admin and thus her username is Jane_Admin. Add her to the Domain admins security group. This is the administrator account. 
</p>
<br />

<p>
<img src="https://i.imgur.io/RtnEFb3_d.webp?maxwidth=640&shape=thumb&fidelity=medium" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join Client-1 to the domain, "mydomain.com," from the Azure portal. Change Client-1's DNS settings to the Domain Controller's private IP address. Restart Client-1 in the Azure portal. Go to settings = About = Rename this PC to change the domain. Complete the credentials from mydomain.com/labuser. Client-1 became a composing part of mydomain.com. Log into Client-1 = Open system properties = Remote Desktop. Permit domain users access to remote desktop. Non-administrative users possess remote desktop on Client-1. 
</p>
<br />

<p>
<img src="https://i.imgur.io/JEV3mA2_d.webp?maxwidth=640&shape=thumb&fidelity=medium" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Input the script into Powershell which produce users into the Domain. Choose one of the users and Remore Desktop Protocal into Client-1. The Powershell script generated a user "bab.hubo," which authorize consent into Client-1 with his credentials as an ordinary user. 
</p>
<br />
