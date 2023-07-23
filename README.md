# Minikube Cheatsheet

This is a cheatsheet for Minikube.

---
# Installation
## Prerequisite

Install [Docker](https://phucbone.github.io/DockerCheatsheet/) before minikube.

## Install On Linux

```bash
# Install using binary.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Install minikube using debian package.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb

# Install minikube using rpm package.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -Uvh minikube-latest.x86_64.rpm
```

## Install On Mac

```bash
# Install using binary on amd64.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

# Install using binary on arm.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-arm64
sudo install minikube-darwin-arm64 /usr/local/bin/minikube

# Install with homebrew on either arm or amd64.
brew install minikube
```

---
# Kubectl
## Run Kubectl Command

```bash
# Run kubectl command.
minikube kubectl -- <kubectl commands>
```

## Set Up Kubectl Alias

```bash
# Set up kubectl alias for easy use.
alias kubectl="minikube kubectl --"
```

---
# Cluster

```bash
# Start minikube cluster.
minikube start

# Pause Kubernetes without impacting deployed applications.
minikube pause

# Unpause a paused instance.
minikube unpause

# Halt the cluster.
minikube stop

# Delete the cluster.
minikube delete

# Upgrade your cluster.
minikube start --kubernetes-version=latest

# Start another cluster.
minikube start -p cluster2

# Show the current active profile.
minikube profile

# List all profiles.
minikube profile list

# Switch the active profile.
minikube profile <profile-name>
```

---
# Addons

```bash
# List all addons.
minikube addons list

# Enable an addon.
minikube addons enable <addon-name>

# Enable an addon at the cluster startup time.
minikube start --addons <addon-name>

# If an addon exposes a browser endpoint, you can quickly open it with.
minikube addons open <addon-name>

# Disable an addon.
minikube addons disable <addon-name>
```

---
# Configs

```bash
# Set the memory limit (requires a restart).
minikube config set memory <size-in-bytes>

# Set the cpu limit (requires a restart).
minikube config set cpus <number-of-cores>

# Get the current config for a field (e.g., memory or cpu).
minikube config <field-name>

# Show the current config.
minikube config view
```

---
# Dashboard
## Minikube On Local

```bash
# Show the dashboard (if you are not using Minikube locally).
minikube dashboard
```

## Minikube On Remote

```bash
# Get a dashboard url.
minikube dashboard --url

# Forward your port.
minikube kubectl proxy -- --address='0.0.0.0' --disable-filter=true

# Then your minikube dashboard can be accessed from the following url.
# (The following command can run from your Mac laptop. If you are not using a Mac laptop, copy the url to your browser)
open "http://{your-minikube-host-ip}:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/"
```

[Back to Cheatsheets Page](https://phucbone.github.io/Cheatsheets/)

[Back to Main Page](https://phucbone.github.io/)
