# 🌐 CCN Enterprise Network Project (EVE-NG Based)

This is a full-scale enterprise network simulation built in *EVE-NG* for a fictional organization called *CCN*. The network spans two major sites:

- 🏢 *Mumbai (Head Office)*
- 🏬 *Pune (Branch Office)*

This project demonstrates real-world enterprise network design, security enforcement using ACLs, domain-name-based access, DMZ services, VLAN segmentation, and inter-site communication.

---

## 🧰 Tools & Technologies

- *Platform:* EVE-NG (Emulated Virtual Environment for Network Labs)
- *Devices:* Cisco Routers, Switches, End Devices, DNS/NTP/DHCP Servers
- *Key Features:*
  - Static Routing
  - VLANs & VTP (Server/Client/Transparent)
  - DHCP from DNS Server
  - DNS + NTP Synchronization
  - NAT (Dynamic PAT & Static NAT for DMZ)
  - ACLs (Access Control Lists) on R1 with domain-based access
  - DMZ Hosting
  - EtherChannel (PAgP, LACP, ON Modes)

---

## 🌐 IP Addressing Overview

### Mumbai Site:

- *LAN:* 192.168.100.0/24
- *DMZ:* 172.16.10.0/24
- *WAN:* 200.200.200.0/24
- *Inter-Router Link:* 192.168.12.0/30

### Pune Site:

- *LAN:* 192.168.200.0/24
- *WAN Links:* 
  - 200.1.30.0/29 (ISP1 to R5)
  - 192.168.53.0/30 (R5-R3), 54.0/30 (R5-R4), 43.0/30 (R3-R4)
  - 36.0/30 (R3-R6), 46.0/30 (R4-R6)

---

## 🖥 DMZ Servers (172.16.10.0/24)

| Hostname           | IP             | Function           |
|--------------------|----------------|--------------------|
| ccn.crm.com        | 172.16.10.1    | CRM Server         |
| ccn.market.com     | 172.16.10.2    | Market Services    |
| ccn.erp.com        | 172.16.10.3    | ERP Server         |
| ccn.hr.com         | 172.16.10.4    | HR Server          |
| ntp                | 172.16.10.5    | NTP Server         |
| ccn-dns            | 172.16.10.6    | DNS + DHCP Server  |

---

## 🔐 Access Control Policy (ACL Highlights)

| Department        | Destination Server      | Access Permissions                   |
|------------------|--------------------------|--------------------------------------|
| SALES (Mumbai)   | CRM (ccn.crm.com)        | HTTPS + Ping                         |
| MARKET (Mumbai)  | DIGI (ccn.market.com)    | All Access + Ping                    |
| ACC (Mumbai)     | ERP (ccn.erp.com)        | HTTP, HTTPS + Ping                   |
| IT               | All DMZ Servers          | SSH, HTTPS + Ping                    |
| HR               | HR Server Only           | HTTPS + Ping                         |
| INTER PCs        | HR Server                | HTTP (Unsecure GUI) + Ping           |
| Pune PCs         | Mumbai DMZ Servers       | HTTPS (via domain name)              |
| Public Servers   | SBI, GST, ADBOE, LinkedIn| HTTPS + Ping as per role             |

(See full ACLs: NAT_and_ACL/ACLs_R1.txt)

---

## 📂 Repository Structure


---

## ✅ Testing Highlights

All the following functions were tested and verified:

- ✅ DNS resolution using domain names
- ✅ ACL enforcement based on department and domain
- ✅ Secure GUI and SSH access to DMZ servers
- ✅ NTP synchronization across switches and routers
- ✅ NAT (PAT for LAN PCs, Static NAT for DMZ servers)
- ✅ WAN communication between Mumbai & Pune

(See: Documentation/Testing_Result.md)

---

## 🧠 Project Purpose

This project was created to simulate a *secure and scalable enterprise network*, showcasing core concepts in:
- Routing
- VLAN & Layer 2 design
- NAT/ACL/DMZ
- Domain-based access security
- Inter-site communication via WAN
- Real-world firewall-level access control logic

---

## 👨‍💻 Author

*Name:* Suraj Kks  
*Role:* Network & Cybersecurity Learner  
*Tools Used:* EVE-NG, Cisco CLI, Wireshark (for testing)  
*Location:* India  
*Year:* 2025

---

## 🖼 Preview

![Network Topology](Topology/CCN_Topology_Image.png)

---

## 📘 Related Files

- [📄 Task_List.md](Documentation/Task_List.md) – Full network requirements  
- [✅ Testing_Result.md](Documentation/Testing_Result.md) – Test case output & results  
- [🔐 ACLs_R1.txt](NAT_and_ACL/ACLs_R1.txt) – All ACL policy commands

