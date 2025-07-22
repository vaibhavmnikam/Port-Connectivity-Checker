# 🔍 Ansible Project: Port Connectivity Checker

This repository contains Ansible playbooks designed to test TCP port connectivity from one or more source servers (`servera`) to a list of destination servers (`serverb`) using `nc` (netcat).

## 📁 Project Contents

- `check_ports_with_audit_report.yml`  
  A playbook that:
  - Runs from one or more `servera` nodes
  - Tests connectivity to `serverb` targets
  - Logs results in CSV format
  - Fetches the final report back to the Ansible control node

- `folderstructure.yml`  
  An optional playbook for setting up standard directory structures and access controls (ACLs).

## 🗂 Inventory Example

```ini
[servera]
10.200.150.133
[serverb]
10.200.150.134
10.200.150.135
10.200.150.136
...

🚀 Running the Playbook

To run the port connectivity check:

ansible-playbook -i hosts check_ports_with_audit_report.yml

✅ This will:

    Execute port checks from all servera hosts

    Check specified ports (default: 22)

    Generate a local CSV report named portreport_check.csv

📊 Sample CSV Output

source_ip,destination_ip,port,result
10.200.150.133,10.200.150.135,22,success
10.200.150.133,10.200.150.136,22,failure

📦 Requirements

    Ansible 2.9+

    nc (netcat) installed on servera hosts

    SSH access between control node and all servera nodes

📌 Notes

    You can modify the playbook to scan additional ports (e.g., 80, 443).

    The report is saved locally on the Ansible control machine.

    Designed for audit/compliance and pre-deployment validation use cases.

🤝 Contributing

Contributions are welcome! Feel free to open issues, improve documentation, or submit pull requests.
