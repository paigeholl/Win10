# Creating a Windows 10 VM on VirtualBox

This guide walks through setting up a Windows 10 virtual machine and connecting it to a domain controller in a company network environment.

## Introduction

The final step in our company network project is adding client computers. A company network isn't complete without workstations that users can access.

## Creating the Virtual Machine

1. From the VirtualBox Details menu, select **New**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_zveik9Yp47bt4dYNWV.png width=400px>

2. In the pop-up window:
   - Name the VM as desired
   - Select **Windows 10 (64-bit)** from the dropdown menu
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_jqwDeXCKY8P7etEjv3.png width=400px>

3. Click **Next**
4. Configure hardware settings: 
   - Set **Base Memory (RAM)** to `2048MB` 
   - Set **Processors** to `3` 

> **Note:** Adjust these values based on your host system's available resources
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_9WyV78DECbUY6oNAhf.png width=400px>

6. Click **Next**
7. Accept the default settings in the 'Virtual Hard Disk' section
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_pJQkz6ODJFJAXWNMdW.png width=400px>

8. Click **Next** and then **Finish**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_nv63rKvdKKkaSKHMFJ.png width=400px>

## Configuring VM Settings

1. Select the VM and open **Settings**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_36WV2EXDth7nKUwrdm.png width=400px>

2. Under **Advanced**, set both **Shared Clipboard** and **Drag'n'Drop** to **Bidirectional**

   This enables copy/paste and file transfer between host and guest systems
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_7fozfmWmq5IpyaxWFp.png width=400px>

3. Select **Network** and change **Adapter 1** to **Internal Network**

   This will allow connection to the Domain Controller for internet access
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_FiuSgye7N2Za57xROs.png width=400px>

4. Click **OK**

## Installing Windows 10

1. Double-click the VM to start it
2. Select your downloaded Windows 10 ISO file when prompted
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_1jiRE1SfoB2SQXquxi.png width=400px>

3. Click **Start**

4. Select **Next** and then **Install Now**
5. Select **I don't have a product key**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_bcaegEFXueIdPbXIWW.png width=400px>

6. Choose **Windows 10 Pro** (required for domain connectivity)
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_a7rhq0KgdxdZgdJbld.png width=400px>

7. Accept the license terms and click **Next**
8. Select **Custom: Install Windows only (advanced)**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_QbyK5I8fkBG8ZNHfH3.png width=400px>

9. Click **Next** to begin installation
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_6WMcNLjTjh28iUvusY.png width=400px>

10. Follow the on-screen setup:
    - Select language and other preferences
    - Choose **Set up for personal use**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_Roie8wNT05yLZg7mWF.png width=400px>
 
11. Select **Offline Account**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_hZPnEChWGkfdoBiwvN.png width=400px>

12. Choose **Limited Experience**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_1lYN0end4F47oKIx6Q.png width=400px>

13. Enter a computer name (e.g., "user")
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_RzDHa9rUicdEXdAI3a.png width=400px>

14. Skip password creation if desired
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_zBw4HTXQwvuRfBWpOs.png width=400px>

15. Decline privacy settings and additional offers

## Joining the Domain

1. Start your Domain Controller VM (if not already running)

   Note: You may need to restart your physical machine and start the DC first if performance is an issue
2. Verify network connectivity:
   - Open Command Prompt
   - Run `ipconfig` and `ping 8.8.8.8` to confirm network connectivity
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_mdRCgJQLOYRrbE1IdM.png width=400px>

3. Change the computer name and join the domain:
   - Right-click the Start menu and select **System**
   - Scroll down and select **Rename this PC (advanced)**
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_AGj8uxcDKFZGmdTdRx.png width=400px>

4. Click **Change** to modify computer name
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_BXDfbwrfT2gy4A8OCi.png width=400px>

5. Select **Domain** option and enter your domain name
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_TiZbjnrJE2RKFzDzQW.png width=400px>

6. Enter domain admin credentials when prompted
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_gT5tfumHvXDLPk6RsH.png width=400px>

## Verifying Domain Integration

While the Windows 10 VM restarts, check the Domain Controller to confirm proper integration:

1. Open DHCP Management:
   - Navigate to Scope > Address Leases
   - Verify the new computer has received an IP address
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_PJBKSiZ3V7LWki6DZY.png width=400px>

2. Open Active Directory Users and Computers:
   - Navigate to Start > Windows Administrative Tools > Active Directory Users and Computers
   - Under Computers, verify the Windows 10 VM is now listed
<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_3IpqXJn5UNqitxVdDU.png width=400px>

## Conclusion

The Windows 10 VM is now successfully joined to the domain. You can sign in with any of the domain accounts created earlier in this project.

