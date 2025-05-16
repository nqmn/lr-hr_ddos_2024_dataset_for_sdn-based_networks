# LR-HR DDoS 2024 Dataset for SDN-Based Networks Proceprocessing Steps

This repository contains a Jupyter Notebook demonstrating preprocessing steps for the LR-HR DDoS 2024 Dataset for SDN-Based Networks. The notebook includes code for loading, cleaning, feature selection, and exporting the dataset, designed for research on DDoS detection in SDN environments.

## Features
- Dataset Loading: Reads the LR-HR DDoS 2024 CSV dataset using pandas.
- Exploratory Data Analysis: Basic inspection (shape, head/tail, summary statistics, protocol/label distributions).
- Data Cleaning: Checks for missing values.
- Manual Feature Selection: Drops irrelevant columns (protocol, srcport, dstport) for binary classification tasks.
- Export: Saves the cleaned dataset as a new CSV file.

## About Dataset

Taken from:
```
https://www.kaggle.com/datasets/abdussalamahmed/lr-hr-ddos-2024-dataset-for-sdn-based-networks
```

The landscape of network management has been transformed by the emergence of Software-Defined Networking (SDN), providing unparalleled adaptability. Yet, this progress also exposes networks to vulnerabilities, necessitating robust security measures. Understanding Distributed Denial-of-Service (DDoS) attacks, especially in SDN environments, is critical for defense strategies. Introducing LR-HR DDoS 2024, a comprehensive dataset encompassing both Low-Rate and High-Rate DDoS attacks within SDN contexts. This dataset reflects real-world conditions, integrating diverse attack vectors and intensities. Methodically constructed, it documents attack generation, network setup, and parameters for efficient utilization.

LR-HR DDoS 2024 addresses the demand for specialized SDN-derived datasets. It spans various attack categories, employing tools like iPerf, Scapy, and Hping3 to generate network flows, accounting for SDN architecture intricacies. Flows are bidirectionally calculated, with features extracted into a CSV file comprising 22 statistical attributes, categorized into eight groups:

- Packet-Based Attributes: Total packet counts in forward and backward directions.
- Network Identifiers Attributes: IP addresses, port numbers, and protocol types.
- Sub flow Descriptors Attributes: Packet and byte counts for subflows.
- Interarrival Time Attributes: Interarrival time details.
- Bytes-Based Attributes: Total byte counts in both directions.
- Flow Timers Attributes: Duration details including active and inactive periods.
- Flow Descriptors Attributes: Packet and byte counts for flows.
- Flag Attributes: Flags like SYN, RST, Push, etc.

The dataset generation process involved:

- Creation of network topologies using Mininet with Ryu controller, OpenFlow Switch, hosts, and servers, followed by traffic transmission.
- Collection of flow and port statistics via a Python script.
- Saving statistics in a CSV file.
- Generating normal traffic using iPerf (TCP, UDP, ICMP) and malicious traffic using Scapy and Hping3 (low and high-rate DDoS).
- Periodic collection of flow statistics.
- Extracting 22 features from controller and network traffic.
- Labeling traffic as normal (0) or malicious (1).
- Running simulations for 2 hours, resulting in about 2,900,000 instances (124,000 rows, 24 columns).
- The dataset encompasses wire and wireless topologies, combining normal and malicious traffic. It comprises 145,614 packets collected over the simulation, with 78,733 normal and 61,881 malicious packets. The traffic involves 56 hosts, each assigned IP addresses from 10.0.0.1 to 10.0.0.255.
