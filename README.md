```markdown
# Backup Setup Documentation: Windows Server 2019 to NAS

## System Information

- NAS IP Address: 192.168.1.100
- Windows Server 2019 IP Address: 192.168.1.10
- User Account: sysadmin (same on both NAS and Windows Server)
- Password: Pa@ssW0rd@11

---

## 1. Preparing the NAS

### 1.1 Create a User Account on NAS
- Account Name: sysadmin
- Password: Pa@ssW0rd@11

### 1.2 Create a Shared Folder on NAS
- Folder Name: serverbackupcollection

### 1.3 Grant Permissions
- Share the folder `serverbackupcollection` with the `sysadmin` account.
- Grant Read and Write permissions to the `sysadmin` account.

---

## 2. Preparing Windows Server 2019

### 2.1 Create a User Account on Windows Server
- Account Name: sysadmin
- Password: Pa@ssW0rd@11

### 2.2 Test Network Connectivity to NAS
1. Open Command Prompt on Windows Server.
2. Ping the NAS IP address:
   ```bash
   ping 192.168.1.100
   ```

### 2.3 Access the Shared Folder on NAS
1. Open File Explorer on Windows Server.
2. In the address bar, type:
   ```bash
   \\192.168.1.100\serverbackupcollection
   ```
3. Verify access by creating a test folder:
   - Folder Name: 192.168.1.10
   - Ensure you have Write permissions (if successful, the folder will be created).

---

## 3. Configuring the Backup on Windows Server 2019

### 3.1 Open Windows Server Backup
1. Click Start and search for Windows Server Backup.
2. Open the Windows Server Backup application.

### 3.2 Start the Backup Configuration
1. On the left navigation panel, click Local Backup.
2. On the right sidebar, click Backup Schedule.
3. On the Getting Started page, click Next.

### 3.3 Select Backup Type
1. Choose the Full Server (recommended) radio button.
2. Click Next.

### 3.4 Set Backup Time
1. Choose Once a day.
2. Set the backup time to 9:00 PM.
3. Click Next.

### 3.5 Select Backup Destination
1. Choose Back up to a shared network folder.
2. Click OK on the pop-up message.

### 3.6 Specify Destination Location
1. In the location field, enter:
   ```bash
   \\192.168.1.100\serverbackupcollection
   ```
2. Click Next.

### 3.7 Enter User Credentials
1. When prompted for credentials, enter:
   - Username: sysadmin
   - Password: Pa@ssW0rd@11
2. Click OK.

### 3.8 Finish the Backup Configuration
1. Click Finish.
2. A message will appear:  
   "Status: You have successfully created the backup schedule."
3. Click Close.

---

## 4. Conclusion

The backup schedule is now set. Windows Server 2019 will automatically back up to the NAS at 9:00 PM every day, using the credentials provided. Ensure that the NAS is powered on and the network connection remains stable for the backup to complete successfully.

```

---
