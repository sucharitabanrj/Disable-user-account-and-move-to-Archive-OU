# Disable-user-account-and-move-to-Archive-OU
Disable user account and move to Archive OU
**Step-by-Step Guide to Disabling and Archiving User Accounts**

This guide will walk you through the process of using the provided PowerShell script to disable user accounts in Active Directory and move them to an "Archived" Organizational Unit (OU).

Prerequisites:
1.	Active Directory Module: Ensure you have the Active Directory Module for PowerShell installed on the computer where you will run the script. You can install it using the following command in an elevated PowerShell window:
Install-Module -Name ActiveDirectory
2.	Permissions: The user account running the script must have sufficient permissions in Active Directory to disable user accounts and move them to another OU. Typically, this requires being a member of the "Domain Admins" or a similar group with delegated permissions.
3.	CSV File: Prepare a CSV file (e.g., upn.csv) containing the User Principal Names (UPNs) of the users you want to disable and archive. The CSV file should have a column named upn where you list the UPNs, one per row.

    Example CSV Content:
    upn
    user1@yourdomain.com
    user2@yourdomain.com

Steps:
1.	Save the Script: Copy the provided PowerShell script and save it as a .ps1 file.
2.	Place the CSV File: Place the prepared CSV file (upn.csv) in the location specified in the $inputFile parameter within the script (or modify the $inputFile parameter to point to the correct location of your CSV file).
3.	(Optional) Change Target OU: If you want to move the disabled users to a different OU than the default one specified in the $TargetOU parameter, modify this parameter within the script to reflect the correct distinguished name (DN) of your desired target OU.
4.	Open PowerShell as Administrator: Right-click on the PowerShell icon and select "Run as administrator".
5.	Navigate to Script Location: Use the cd command to navigate to the directory where you saved the script. For example:
    cd C:\Scripts\ 
6.	Execute the Script: Run the script using the following command:
    .\ DisableUserAccountand Move.ps1
    o	If you modified the $inputFile or $TargetOU parameters within the script, you don't need to provide them as arguments when running the script.
    o	If you want to provide the parameters explicitly when running the script, you can do so like this:
    .\ DisableUserAccountand Move.ps1-inputFile "C:\Your\Path\To\upn.csv" -TargetOU "OU=YourArchivedOU,DC=yourdomain,DC=com"
7.	Observe the Output: The script will process each UPN in the CSV file.
    o	You'll see messages indicating if a user was found or not.
    o	If a user is found, the script will attempt to disable their account and move them to the Archived OU.
    o	You'll see warning messages if there are any errors during the process.
    o	Finally, you'll see success messages for each user indicating they have been disabled and moved.

Important Notes:
•	Backup: It's highly recommended to take a backup of your Active Directory before running any scripts that modify user accounts or their locations.
•	Testing: Always test the script in a non-production environment first to ensure it works as expected and to avoid any unintended consequences.   
•	Permissions: Double-check that the user account running the script has the necessary permissions in Active Directory to disable user accounts and move them to another OU.
•	CSV Accuracy: Make sure the UPNs in your CSV file are accurate and correspond to the users you intend to disable and archive.

