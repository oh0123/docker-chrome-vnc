# Easily launch ephemeral headed Chrome instances
Launch headed Chrome in a Docker container, start a VNC server, and get the remote debugging websocket endpoint back.
This program solves the problem of not being able to run Playwright in headless=false mode from a Docker container.

By using this, you agree to Google Chrome terms: https://www.google.com/chrome/terms/

## Install
Simply clone and build the docker image.
```bash
git clone https://github.com/gbiz123/docker-chrome-vnc/
cd docker-chrome-vnc
docker build -t chrome-gui .
chmod +x run-chrome-gui.sh
```

## Launch
Run the script to get the container ID and the websocket URL. The websocket URL can be used for Playwright automation over Chrome CDP.
```bash
./run-chrome-gui.sh 9222 5900 # Specify port for remote debugging
>>> {"containerId":de66831e80a5c0c6645e8240276549ea40ca18a30e816a100c5c28c4e139bfe3,"wsEndpoint":ws://localhost:9222/devtools/browser/8c6ff95f-f609-49eb-b701-d46b3e0e1c89}
```

## Connect VNC
Use any VNC client to visualize and interact with the browser.
```bash
vncviewer localhost:5900
```
