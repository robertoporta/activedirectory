# <p align="center">
<img width="644" height="333" alt="Image" src="https://github.com/user-attachments/assets/5ba3a47e-65b6-4133-8cc8-b955b5e11c18"/>
</p>

<h1>Deploying and Configuring Active Directory and Users</h1>
This project demonstrates how to install, configure, and manage Active Directory Domain Services (AD DS) on a Windows Server virtual machine hosted in Microsoft Azure. The goal is to show the process of setting up a new domain, promoting the Azure VM to a domain controller, and creating and managing user accounts within the domain. It demonstrates how centralized user management and authentication work in an enterprise environment using Active Directory.
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop (RDP)
- Microsoft Active Directory Domain Services (AD DS)
- Power Shell
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>Active Directory Configuration and User Management</h2>

<p>
<img width="1168" height="654" alt="Image" src="https://github.com/user-attachments/assets/0f26bc6a-ca6f-46bb-a6a4-06e89b5a0f36" />
</p>
<p>
- First, a resource group needs to be created in Azure. This group acts as a container that holds all related resources for the project, making it easier to manage, monitor, and organize everything connected to the Active Directory setup.
</p>
<br>

<p>
<img width="1169" height="657" alt="Image" src="https://github.com/user-attachments/assets/e8d7a487-c4ac-47e7-bf3d-f04972741fb3" />
</p>
<p>
- Then, I create a virtual network to allow the virtual machine and other future resources to communicate securely within the same network. This setup provides the foundation for domain connectivity and simulates a real on-premises environment in the cloud.
  
</p>
<br>

<p>
<img width="1171" height="655" alt="Image" src="https://github.com/user-attachments/assets/222d81fa-f850-42b7-9dc4-6ed7ec4497d7" />
</p>
<p>
- After that, I create the virtual machine that will act as the Domain Controller and name it “dc-1.” I also select the appropriate region and Windows Server image to ensure compatibility and optimal performance within the Azure environment.  
</p>
<br>

<p>
<img width="1177" height="577" alt="Image" src="https://github.com/user-attachments/assets/7ed8aab5-c8b9-4d06-8d69-0299a657713c" />
</p>
<p>
 - I continue by selecting the necessary memory size for smooth operation, creating a secure username and password for administrator access, and configuring the required inbound port settings to allow remote management through RDP. 
</p>
<br>

<p>
<img width="1167" height="655" alt="Image" src="https://github.com/user-attachments/assets/caf00be3-aa92-4071-9e7b-cd25901cf2ff" />
</p>
<p>
- Next, I create another virtual machine that will act as the client system and name it “client-1.” I make sure it’s placed in the same virtual network and region as the domain controller to allow proper communication between both systems.  
</p>
<br>

<p>
<img width="1165" height="654" alt="Image" src="https://github.com/user-attachments/assets/5b9fad0f-a6ab-43c7-b630-63d5b1a9d748" />
</p>
<p>
- Then, I select the appropriate Windows image and memory size for the client machine to ensure stable performance and compatibility during domain testing and user authentication.  
</p>
<br>

<p>
<img width="1168" height="655" alt="image" src="https://github.com/user-attachments/assets/510846e4-82a2-4fd8-8175-fca5143df3bb" />
</p>
<p>
- Finally, I change the private IP settings of the Domain Controller to static, ensuring its internal address remains the same even after restarts. A Domain Controller must always have a fixed IP so other systems can reliably locate it for DNS resolution, authentication, and communication within the domain.
</p>
<br>

<p>
<img width="1168" height="655" alt="Image" src="https://github.com/user-attachments/assets/4f4990f9-8b7b-482e-a691-23fc9a0e630c" />  
</p>
<p>
- After all resources are created, I can now access both virtual machines through Remote Desktop. In the domain controller, I open Server Manager and enable the Active Directory Domain Services role, which installs the core components needed to create and manage a Windows domain.  
</p>
<br>

<p>
<img width="1170" height="656" alt="Image" src="https://github.com/user-attachments/assets/60fed0c5-43bb-4f1a-b6e4-ad1525a4ebd6" />  
</p>
<p>
- I then add a forest, which is the top-level structure in Active Directory that contains and manages one or more domains under a single security boundary. I also specify the root domain as "mydomain.com," which serves as the main domain of the forest and the foundation for all user accounts, computers, and organizational units that will be created later.  
</p>
<br>

<p>
<img width="1172" height="659" alt="Image" src="https://github.com/user-attachments/assets/5f1e71ff-779d-41d1-b26f-06f7a6ae756e" />
</p>
<p>
- Next, I create a new administrator user within Active Directory and set the appropriate properties such as username, password, and organizational unit. This account will serve as the main domain admin for managing users, computers, and security settings in the environment. Creating a separate admin user, rather than relying on the default Administrator account, is a best practice that provides better control and accountability.
</p>
<br>

<p>
<img width="1166" height="654" alt="Image" src="https://github.com/user-attachments/assets/bcde39be-6f36-4b88-ab78-fcabc8755c21" />
</p>
<p>
- Then, I open PowerShell as an administrator and run a script that automatically creates hundreds of user accounts in Active Directory. This script uses commands like <code>New-ADUser</code> to generate accounts with predefined settings such as names, usernames, and passwords. The purpose of this step is to simulate a real-world environment by quickly populating the directory with many users, allowing for realistic testing and management practice throughout the project.
</p>
<br>

<p>
<img width="1170" height="660" alt="Image" src="https://github.com/user-attachments/assets/17ed2371-fb7d-4681-a89b-e71396d1cafd" />  
</p>
<p>
- Finally, we can see the newly created users listed within Active Directory Users and Computers. This confirms that the PowerShell script ran successfully and that the users were added to the domain, completing the setup of the simulated environment.
</p>
<br>

<br />
