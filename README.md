# Firewall-on-Windows
I USE WINDOWS FIREWALL AND GAINED SOME EXPERIENCE
Firewall Configuration and Traffic Filtering Report
1. Open Firewall Configuration Tool
Windows:
- Open Windows Security → Firewall & network protection → Advanced settings
- Or open Run (Win + R) and type: wf.msc
Linux (UFW):
- Open terminal and check if UFW is installed:
sudo ufw status
2. List Current Firewall Rules
Windows (PowerShell):
netsh advfirewall firewall show rule name=all
Linux (UFW):
sudo ufw status numbered
3. Add a Rule to Block Inbound Traffic on Port 23 (Telnet)
Windows:
netsh advfirewall firewall add rule name="Block Telnet" dir=in action=block protocol=TCP
localport=23
Linux (UFW):
sudo ufw deny 23/tcp
4. Test the Rule
Use Telnet to test connectivity:
telnet localhost 23
The connection should fail, confirming that the port is blocked.
5. Add Rule to Allow SSH (Port 22)
Windows (Optional):
netsh advfirewall firewall add rule name="Allow SSH" dir=in action=allow protocol=TCP
localport=22
Linux (UFW):
sudo ufw allow 22/tcp
6. Remove the Test Block Rule (Restore Original State)
Windows:
netsh advfirewall firewall delete rule name="Block Telnet"
Linux (UFW):
sudo ufw delete deny 23/tcp
7. Document Commands or GUI Steps Used
| Step | OS | Method | Command / Action |
|------|----|---------|------------------|
| 1 | Windows | GUI / CLI | wf.msc |
| 2 | Windows | CLI | netsh advfirewall firewall show rule name=all |
| 3 | Both | CLI | Block port 23 |
| 4 | Both | Test | telnet localhost 23 |
| 5 | Linux | CLI | sudo ufw allow 22/tcp |
| 6 | Both | CLI | Remove test rule |
| 7 | Both | Summary | Documented commands |
8. Summary: How Firewall Filters Traffic
A firewall monitors and controls network traffic based on predefined security rules. It:
- Filters packets based on IP address, port, and protocol.
- Blocks unauthorized access while allowing trusted communication.
- Prevents attacks like port scanning and unauthorized remote access.
- Acts as a barrier between trusted internal networks and untrusted external sources.<img width="1373" height="643" alt="Screenshot 2025-10-27 073643" src="https://github.com/user-attachments/assets/c0147273-1cd7-4ebb-b52f-77a2384337fb" />
<img width="1372" height="628" alt="Screenshot 2025-10-27 073609" src="https://github.com/user-attachments/assets/20aaf4b5-7191-4dc6-88ee-23a6839c2861" />
<img width="758" height="549" alt="Screenshot 2025-10-27 073541" src="https://github.com/user-attachments/assets/efe9b4a0-fed2-4f2e-9c7a-167b3a0e4186" />
<img width="1332" height="504" alt="Screenshot 2025-10-27 073508" src="https://github.com/user-attachments/assets/888e145f-3b6a-4a3a-bfca-1cc3db64e698" />
