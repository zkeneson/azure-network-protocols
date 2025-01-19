<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Windows VM
- Create Linux Ubuntu VM
- Observe ICMP traffic using WireShark
- Configure firewall (Network Security Group)
- SSH into Ubuntu VM from Windows VM
- Observe DNS traffic using nslookup in PowerShell

<h2>Actions and Observations</h2>

<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/3610cfa4-3bb6-4b08-ae8f-36bfb2bde840" />

</p>
<p>
Create a Windows 10 virtual machine. Make sure to choose the Resource Group you created for these virtual machines. Also, keeping the Region the same as your RG is important.  
</p>
<br />

<p>
<img width="957" alt="image" src="https://github.com/user-attachments/assets/7bafc90d-c1cb-4271-b758-1c5c9460d8b5" />

</p>
<p>
Here is where we create the Ubuntu VM. Again, match the RG and Region just like when creating the Windows 10 VM.
</p>
<br />

<p>
<img width="1919" alt="image" src="https://github.com/user-attachments/assets/96d63300-ae37-454c-8692-b5492fe9dbe6" />

</p>
<p>
Download WireShark within the Windows VM. Start capturing the network traffic by clicking the fin in the top left of the screen under File. Then, filter the traffic for ICMP. Next, open Powershell and ping the private IP adress of the Ubuntu VM. Start a continuous ping between the two VMs.
</p>
<br />

<p>
<img width="955" alt="image" src="https://github.com/user-attachments/assets/22bfc015-be9c-4647-8dea-8c0317e4cecc" />


</p>
<p>
In Azure, set the inbound security rules for the Ubuntu VM to deny ICMPv4 traffic. 
</p>
<br />

<p>
<img width="1916" alt="image" src="https://github.com/user-attachments/assets/e1e291cc-0007-4390-a167-7eb9123cba4b" />


</p>
<p>
Observe in WireShark the pings are timed out, meaning the Network Security Group firewall settings are working correctly. 
</p>
<br />

<p>
<img width="1917" alt="image" src="https://github.com/user-attachments/assets/debb145c-c372-4034-a64f-8ef18698c950" />


</p>
<p>
Filter for SSH network traffic. Use PowerShell to try to ping the Ubuntu VM via SSH protocol. 
</p>
<br />

<p>
<img width="1919" alt="image" src="https://github.com/user-attachments/assets/15454a0a-4564-4720-942c-55a51b514aae" />



</p>
<p>
Filter for DNS network traffic. Use PowerShell to run nslookup for any website. Observe the IP address and network traffic.
</p>
<br />

