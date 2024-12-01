# Multi-Mode Digital Voice Reflector Setup Playbook

This Ansible playbook automates the setup of a multi-mode digital voice reflector that includes **D-STAR**, **YSF**, and **DMR**, along with bridging between these protocols. This enables cross-mode communication for ham radio enthusiasts.

---

## Features
- Sets up and configures an XLX Reflector for D-STAR.
- Installs and configures YSFReflector and YSF2DMR for protocol bridging.
- Configures AMBE transcoding for D-STAR audio streams.
- Integrates with Brandmeister for DMR compatibility.
- Automates SSL setup using Let's Encrypt for secure dashboards.
- Applies necessary firewall rules and validates configuration steps.

---

## Prerequisites
1. **Ansible Installed**: Ensure Ansible is installed on the controller machine.
   - Installation Guide: [Ansible Documentation](https://docs.ansible.com/ansible/latest/installation_guide/index.html)
2. **SSH Access**: Ensure the Ansible controller can SSH into the target server using pre-configured keys.
3. **FQDN and IP Address**: Have your fully qualified domain name (FQDN) and public IP address ready.

---

## Setup
### Variables
Before running the playbook, update the following variables in the playbook file (`reflector_setup.yml`):

- `fqdn`: Your reflector's fully qualified domain name (e.g., `xrf123.example.com`).
- `reflector_ip`: The public IP address of your server.
- `ssl_email`: Email address for obtaining SSL certificates (e.g., `admin@example.com`).
- `xlx_number`: The reflector number you plan to use.
- `dmr_id`: Your DMR ID (from Brandmeister or equivalent).
- `bm_master`: Brandmeister master server (e.g., `3102`).

### Required Ports
Ensure the following ports are allowed in your firewall:
- **TCP**: 22 (SSH), 80 (HTTP), 443 (HTTPS)
- **UDP**: Various ports needed for XLX, YSF, and DMR protocols (refer to playbook for specifics).

---

## Running the Playbook
1. Clone or copy this repository to your Ansible controller machine.
2. Update the inventory file with the target server's details.
3. Run the playbook:
```bash
   ansible-playbook -i inventory build-reflector.yml
```
