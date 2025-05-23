# Linux System Monitoring Dashboard using Prometheus & Grafana

This project demonstrates how to set up a real-time Linux system monitoring stack using **Prometheus**, **Node Exporter**, and **Grafana**. It tracks key system metrics like CPU usage, memory, disk I/O, and network activity, and visualizes them using a fully featured Grafana dashboard.

---

## 📌 Overview

- **Prometheus** collects system metrics.
- **Node Exporter** exposes machine-level statistics to Prometheus.
- **Grafana** visualizes the data in a dynamic dashboard.

---

## ⚙️ Tools & Technologies

- Prometheus v2.52.0
- Node Exporter v1.8.1
- Grafana OSS
- WSL (Ubuntu on Windows)
- Linux shell (Bash)

---

## 🖥️ System Metrics Tracked

- CPU usage and load average
- RAM and Swap usage
- Disk space and I/O
- Network throughput
- Uptime and system info

---

## 📷 Dashboard Screenshot

> Example Grafana Panel:

![System Dashboard](dashboard_ss1.png)

---

## 🛠️ Setup Instructions

### 1. Install Prometheus

```bash
wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
tar xvf prometheus-2.52.0.linux-amd64.tar.gz
cd prometheus-2.52.0.linux-amd64
./prometheus --config.file=prometheus.yml
```

### 2. Install Node Exporter

```bash
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.1/node_exporter-1.8.1.linux-amd64.tar.gz
tar xvf node_exporter-1.8.1.linux-amd64.tar.gz
cd node_exporter-1.8.1.linux-amd64
./node_exporter
```

### 3. Configure Prometheus (`prometheus.yml`)

```yaml
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```

### 4. Install and Start Grafana

```bash
sudo apt install -y software-properties-common
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt update
sudo apt install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

### 5. Import Grafana Dashboard

- Go to `http://localhost:3000`
- Login with `admin` / `admin`
- Import dashboard ID **1860**
- Connect to Prometheus data source

---

## 📁 Project Structure

```
linux-system-monitor/
├── prometheus.yml
├── README.md
├── dashboard-screenshot.png
└── setup/
    ├── prometheus-install.sh (optional)
    └── node_exporter-install.sh (optional)
```

---

## 💡 Author

Samad Mehndi – [LinkedIn](https://linkedin.com/in/samad-mehndi)

---
