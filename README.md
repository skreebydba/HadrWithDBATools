# HadrWithDBATools
Slides and notebooks for Managing SQL Server HADR with DBATools
This project contains two notebooks the following files.

## LogShipping.ipynb
Sets up log shipping for a database
### Requirements
- Two instances of SQL Server
- Agent Service Account must be an AD account
- A file share to hold the log backups
- Read/write permissions to the backup share for the primary Agent Service Account
- Read permissions to the backup share for the secondary Agent Service Account
- Read/write permissions to the copy destination for the secondary Agent Service Account
- DBATools PowerShell module - run ```Install-Module DBATools``` from an Adminstrator PowerShell window to install the module

## ConfigureAg.ipynb
Create a an Availability Group and Dynamic Network Name listener
### Requirements
- Two Windows servers running instances of SQL Server
- Both instances should use the same paths for data and log files
- Windows Server Failover Cluster containing the two SQL nodes wtih no shared storage
- Enable Always On Availability Groups in SQL Server Configuration Manager for both instances
- Grant the following permissions to NT AUTHORITY\SYSTEM
```
GRANT ALTER ANY AVAILABILITY GROUP TO [NT AUTHORITY\SYSTEM]
GO
GRANT CONNECT SQL TO [NT AUTHORITY\SYSTEM]
GO
GRANT VIEW SERVER STATE TO [NT AUTHORITY\SYSTEM]
GO
```