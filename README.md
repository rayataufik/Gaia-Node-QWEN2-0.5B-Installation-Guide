
# Gaia Node QWEN2-0.5B Installation Guide

Node Type: QWEN2-0.5B \
OS: Ubuntu 20.04 / 22.04 / 24.04 \
Spec: 4 Core CPU, 8 GB RAM 




## Prerequisites

Clean Ubuntu server (20.04–24.04) \
User has $sudo access \
At least 10GB+ disk space available

## Register Gaia

Open the link below to register your node and claim rewards:\
👉 https://gaianet.ai/reward?invite_code=RfYVdd
## Setup Gaia Node

#### 1. Uninstall Existing Gaia Node
If you've previously installed a Gaia node, run the following to completely remove it:
```bash
curl -sSfL 'https://github.com/GaiaNet-AI/gaianet-node/releases/latest/download/uninstall.sh' | bash
```
💡 Old node ID does not need to be saved.

#### 2. Update Ubuntu:
Update and upgrade your system to the latest packages:
```bash
sudo apt update && sudo apt upgrade -y
```

#### 3. Reboot VPS / Server / VM:
After upgrading, reboot the machine:
```bash
sudo reboot
```

#### 4. Create Directory for Gaia Node
After reboot, open terminal again and run:
```bash
cd $HOME
mkdir gaia-node-101
```

#### 5. Install Gaia Node
Run the install script and point the base to the directory created:
```bash
curl -sSfL 'https://github.com/GaiaNet-AI/gaianet-node/releases/latest/download/install.sh' | bash -s -- --base $HOME/gaia-node-101
```
Then load your updated shell configuration: 
```bash
source $HOME/.bashrc
```

#### 6. Configure QWEN2-0.5B with Custom Port
##### a. Initialize with config:
```bash
gaianet init --base $HOME/gaia-node-101 --config https://raw.githubusercontent.com/GaiaNet-AI/node-configs/main/qwen2-0.5b-instruct/config.json
```
##### b. Change the default port to 8101:
```bash
gaianet config --base $HOME/gaia-node-101 --port 8101
```
##### c. Re-initialize after port change:
```bash
gaianet init --base $HOME/gaia-node-101
```

### 7. Start Gaia Node
#### a. (Optional) Kill existing process on port 8101:
```bash
sudo lsof -t -i:8101 | xargs kill -9
```
#### b. Start node:
```bash
gaianet start --base $HOME/gaia-node-101
```

### 8. Get Node ID & Device ID
To check your node and device info:
```bash
gaianet info --base $HOME/gaia-node-101
```

### 9. Register Node to Gaia Dashboard
#### 1. Log in or create an account, then go to the Nodes Settings page:
👉 https://www.gaianet.ai/setting/nodes
#### 2. Enter your Node ID and Device ID obtained from the command:
```bash
gaianet info --base $HOME/gaia-node-101
```
