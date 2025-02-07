# InfiniBand tools for Slurm

The tools in this folder may be useful with Slurm on systems with InfiniBand or Omni-Path networks.

This work is based on scripts by Ward Poelmans <ward.poelmans@vub.be> and Max Rutkowski <max.rutkowski@gfz-potsdam.de>.

Usage
-----

The `waitforib.sh` tool waits until at least 1 InfiniBand *link_layer* port is in the `ACTIVE` state.
At that point jobs run by `slurmd` or `NFS network mounts` may be started.

The `waitforib.service` Systemd service delays the `network-online.target` until InfiniBand is active.

Installation
--------------

Copy the script:
```
cp waitforib.sh /usr/local/bin/
chmod +x /usr/local/bin/waitforib.sh
```

Enable the Systemd service:
```
cp waitforib.service /etc/systemd/system/
systemctl enable waitforib.service
```

When the system is rebooted, the `network-online.target` is delayed until InfiniBand/Omni-Path is active.
