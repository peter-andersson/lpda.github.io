---
layout: post
title: "Azure Virtual Machine with Ubuntu - Initial configuration"
date: 2020-07-06
author: Peter Andersson
---

# Description
I have had some problems with using smaller virtual machines in Azure where there is high disk and memory usage from some automatic installed monitor tools. Sometimes I have had to remake the machine and sometime a restart will help.

# Solution
Remove WALinuxAgent and OMSAgent from the virtual machine after first setup.

```sh
# Remove WALinuxAgent
sudo apt purge walinuxagent

# This might not be installed but make sure that it is removed anyways.
wget https://raw.githubusercontent.com/Microsoft/OMS-Agent-for-Linux/master/installer/scripts/onboard_agent.sh

sudo sh onboard_agent.sh --purge

sudo rm –rf /etc/opt/microsoft/omsagent

sudo rm –rf /var/opt/microsoft/omsagent
```