# windows-powertools
Windows PowerShell/other "PowerTools".

My dump for Windows 10 stuff. Mainly PowerShell/CMD stuff.

##Windows Management Instrumentation Command-line (WMIC)
* From within the **wmic cli**:
  * To access the wmic cli, open PowerShell and type: `wmic`
  * To access the help menu, from the wmic cli command prompt, type: `/?`
* Directly from **PowerShell**:
  * To get your computer's serial number, type: `wmic bios get serialnumber`
  * To get a list of running processes, updated every 5 seconds: `wmic process list brief /every:5`
  * To "kill -9" a process by PID: `wmic process [pid] delete`
  * To "killall" a process by name: `wmic process where "name='firefox.exe'" delete`
  * To filter process list by name: `wmic process list brief | select-string "chrome.exe"`
    - Or you can pipe to `find.exe`, although you will (annoyingly) need to escape the quotes with backticks like so:
    ```
     wmic process list brief | find `"chrome.exe`"
     ```
   * Get the manufacturer/model name of your computer: `wmic csproduct get name`
   * Get a bunch more stuff:
   ```wmic computersystem get name,domain,manufacturer,model,numberofprocessors,primaryownername,username,roles,totalphysicalmemory/format:list
   ```
   * Get specific with the cpu:
   ```
   wmic cpu get name,caption,maxclockspeed,deviceid,status/format:list
   ```
   * Disk:
   ```
   wmic diskdrive get name,manufacturer,model,interfacetype,medialoaded,mediatype/format:list
   ```
   * Environment:
   ```
   wmic environment get description,variablevalue/format:list
   ```
   * IDE Controller:
   ```
   wmic idecontroller get name,manufacturer,deviceid,status
   ```
   * Load Order:
   ```
    wmic loadorder get name,driverenabled,grouporder,status
    ```
    * Logical Disk:
    ```
    
    wmic logicaldisk get name,compressed,description,drivetype,filesystem,freespace,supportsdiskquotas,volumedirty,volumename/format:list
    ```
    * Memory:
    ```
    wmic memphysical get caption,location,maxcapacity,memorydevices,memoryerrorcorrection,tag,use/format:list
    ```
    * (Much better) Memory:
    ```
    wmic memorychip get banklabel,capacity,caption,creationclassname,datawidth,devicelocator,formfactor,interleavedatadepth,interleaveposition,manufacturer,memorytype,name,partnumber,positioninrow,serialnumber,speed/format:list
    ```
    * Login details:
    ```
    wmic netlogin get name,fullname,scriptpath,profile,userid,numberoflogons,passwordage,logonserver,homedirectory,primarygroupid/format:list
    ```
    * Network Protocols:
    ```
    wmic netprotocol get caption,description,guaranteessequencing,supportsbroadcasting,supportsencryption,status/format:list
    ```
    * NIC:
    ```
    wmic nic get adaptertype,autosense,name,installed,macaddress,speed
    ```
    * Network Config:
    ```
    wmic nicconfig get macaddress,defaultipgateway,ipaddress,ipsubnet,dnshostname,dnsdomain/format:table
    ```
    * Domain:
    ```
    wmic ntdomain get caption,clientsitename,domaincontrolleraddress,domaincontrollername,status
    ```
    * Total OS Deep Dive Blowout:
    ```
    wmic os get caption,currenttimezone,codeset,countrycode,creationclassname,csname,cscreationclassname,serialnumber,bootdevice,systemdevice,NumberOfUsers,OperatingSystemSKU,Organization,OSArchitecture,OSLanguage,OSProductSuite,OSType,PortableOperatingSystem,DataExecutionPrevention_32BitApplications,DataExecutionPrevention_Drivers,DataExecutionPrevention_SupportPolicy,Debug,Distributed,EncryptionLevel,Manufacturer,MaxNumberOfProcesses,MaxProcessMemorySize,MUILanguages,Name,NumberOfProcesses,NumberOfLicensedUsers,Primary,ProductType,RegisteredUser,SerialNumber,ServicePackMajorVersion,ServicePackMinorVersion,SizeStoredInPagingFiles,Status,SuiteMask,SystemDevice,SystemDirectory,ForegroundApplicationBoost,FreePhysicalMemory,FreeSpaceInPagingFiles,FreeVirtualMemory,InstallDate,LargeSystemCache,LastBootUpTime,LocalDateTime,Locale,SystemDrive,TotalSwapSpaceSize,TotalVirtualMemorySize,TotalVisibleMemorySize,Version,WindowsDirectory/format:list
    ```
    * OS (brief):
    ```
    wmic os get freephysicalmemory,freevirtualmemory,lastbootuptime,numberofprocesses,numberofusers,organization,registereduser,status
    ```
    * Partition info:
    ```
    wmic partition get caption,size,primarypartition,status,type
    ```
    * Printers:
    ```
    wmic printer get deviceid,drivername,hidden,name,portname,printjobdatatype,verticalresolution,horizontalresolution
    ```
    * Sysdriver:
    ```
    wmic sysdriver get caption,name,pathname,servicetype,state,status/format:list
    ```
    * Shares:
    ```
     wmic share get name,path,status
     ```
     * List running services:
     ```
     wmic service get name,caption,state,servicetype,startmode,pathname/format:list
     ```
     * 
     
    Links:
    https://docs.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/using-format-commands-to-change-output-view?view=powershell-5.1
   
    
  
