# AWS Ansible Passwordless Configuration

##  Overview
This project demonstrated how I set up "two AWS EC2 instances" — one as a "control node" and the other as a "target server" — and configured passwordless SSH access. Using Ansible, the control node managed configurations on the target server securely and automatically.

---

##  Steps Implemented

1. Provisioned AWS Instances
   - I created two EC2 instances (Ubuntu).
   - I designated one as the "control node" and the other as the "target server".

2. Configured Passwordless SSH
   - I generated an SSH key pair on the control node.
   - I copied the **public key** into the `~/.ssh/authorized_keys` file of the target server.
   - I verified passwordless login from control → target.

3. Set Up Ansible Inventory
   - I created an inventory file in `~/.ansible/inventory`.
   - I entered the IP address of the target server:
     ```ini
        10.0.4.195    

     ```

4. Wrote Ansible Playbook
   - myfirstplaybook.yml (`setup.yml`):
     ```yaml
     ---
     - name: Install and Start nginx
       hosts: all
       become: true
       become_user: root
     
       tasks:
         - name: Install nginx
           apt:
             name: nginx
             state: present

         - name: Start nginx 
           service:
             name: nginx
             state: started
    
     ```

---

##  Outcome
- Passwordless SSH access was successfully established between the control and target nodes.  
- The Ansible playbook installed and started "nginx" on the target server.  
- The project demonstrated "cloud provisioning, automation, and security best practices."

---

##  Skills Showcased
- AWS EC2 provisioning  
- SSH key management  
- Ansible inventory & playbooks  
- Configuration management & automation  

---
<img width="1366" height="768" alt="Screenshot (1600)" src="https://github.com/user-attachments/assets/6c541acc-1346-4c77-89f8-0d1b7dad798b" />
<img width="1366" height="768" alt="Screenshot (1599)" src="https://github.com/user-attachments/assets/11f1f414-6f88-4957-b7eb-24910520a6e6" />
<img width="1366" height="768" alt="Screenshot (1601)" src="https://github.com/user-attachments/assets/8f952a58-6aa6-49e2-923f-656bb37d5c60" />

##  Future Improvements
- Scale to multiple target servers in the inventory.  
- Use "roles" for cleaner playbook organization.  
- Integrate with **CI/CD pipelines** for automated deployments.  
- Add monitoring (CloudWatch, Prometheus) for observability.  
