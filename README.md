# 🏗️ Implementing Virtual Networking in Azure

**Owner**: Ohilere Imiere Darlington  
 

## 📌 Project Goal
Design and implement a **secure**, **scalable**, and **efficient** virtual networking infrastructure using Microsoft Azure that enables:

- Seamless communication between cloud resources
- Protection with Network Security Groups (NSGs) and Application Security Groups (ASGs)
- DNS zone and record configuration
- Alignment with Azure architecture best practices

---

## 🔧 Architecture Overview

### 📐 Policy Flow Summary
**Scope**:

- Create and configure Azure Virtual Networks (VNets) and Subnets
- Assign/manage public and private IPs
- Implement Network Security Group (NSG)
- Implement Appication Security Group (ASG)
- Use Azure CLI and PowerShell for deployment

## Architectural Diagram
![Architecture Diagram](https://imgur.com/v0qEtyi.png)

---

## 📚 Step-by-Step Implementation Guide

###  Step 1: Create VNet with Subnets (Portal)

1. Sign in to Azure Portal  
2. Create resource group `vnRG`  
3. Create VNet: `CoreServicesVNet`  
4. Add subnets:
   - `SharedServicesSubnet`
   - `DatabaseSubnet`  
5. Download and save deployment template

![Virtual Network](https://imgur.com/QRVjjj7.png) 

---

###  Step 2: Create VNet & Subnets via Template

1. Extract template folder and open `template.json` in VS Code  
2. Modify:
   - Replace `CoreServicesVNet` with `ManufacturingVNet`
   - CIDR `10.20.0.0` → `10.30.0.0`
   - Subnet mappings:
     - `SharedServicesSubnet` → `SensorSubnet1`
     - `DatabaseSubnet` → `SensorSubnet2`
3. Deploy template in Azure Portal with new parameters

![VS Code](https://imgur.com/8D9EKb6.png)
![Template](https://imgur.com/7Ik55wf.png)
![VS Code](https://imgur.com/7AHE2kf.png)
---

###  Step 3: Configure ASG & NSG Communication

1. Create ASG  
2. Create NSG  
3. Associate NSG with `SharedServicesSubnet` in `CoreServicesVNet`  
4. Add NSG rules:
   - Inbound: Allow traffic from ASG
   - Outbound: Deny internet access

![ASG](https://imgur.com/2c1zWwM.png)
![NSG](https://imgur.com/XYTFrJx.png)
![NSG](https://imgur.com/MwXTg4R.png)
![Inbound Rule](https://imgur.com/G3IfPrv.png)
![Outbound Rule](https://imgur.com/ICyphcU.png)
---

###  Step 4: Deploy VMs and Add to ASG

1. Create VM in `DatabaseSubnet` via Portal  
2. Create VM in `SharedServicesSubnet` using CLI in VS Code  
3. Associate the SharedServices VM to ASG

![VM](https://imgur.com/fBjkDf6.png)
![VM](https://imgur.com/gFDksk1.png)
![VM](https://imgur.com/KwofvTu.png)
---

###  Step 5: Configure Azure DNS Zones

1. Configure public and private DNS zones  
2. Link private zone to `ManufacturingVNet` for name resolution

![DNS](https://imgur.com/ecGTsDE.png)
![DNS](https://imgur.com/hV5DMIm.png)
![DNS](https://imgur.com/p5S8Vx5.png)
---

###  Step 6: Assign RBAC to VNet

1. Select `CoreServicesVNet`  
2. Go to Access Control (IAM)  
3. Add Role Assignment (e.g., IT Lab Administrators)

![RBAC](https://imgur.com/Cdt1zLx.png)

---


