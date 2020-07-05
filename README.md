# pve-patch

Removes subscription dialogs, replaces enterprise repository with non-subscription repository and replaces branding. Tested on PVE 6.2-4/9824574A
Current as of July 5, 2020, 11:25AM EST

* This is just a copy of the original repo with my username in place of kosomonavtika's.  
* Also, I didn't like the graphics so I replaced them too, but these are trivial.

This isn't to steal credit, its to have control over the repo source.  
If the source repo has 'bad stuff' added, I have a chance to look at it before it kills my machines.  :)

## Note

Use at your own risk! Read the script before you run it. 

## Install

1. Connect to node via SSH
2. Run

```bash
# if root
wget -qO - https://raw.githubusercontent.com/trevormerritt/pve-patch/master/patch.sh | bash

# if non-root
wget -qO - https://raw.githubusercontent.com/trevormerritt/pve-patch/master/patch.sh | sudo bash
```

## Restore

Enterprise repository

```
mv /etc/apt/sources.list.d/pve-enterprise.list~ /etc/apt/sources.list.d/pve-enterprise.list
```

Branding

```
cp -f /usr/share/pve-manager/images/favicon.ico~ \
/usr/share/pve-patch/images/favicon.ico && \
cp -f /usr/share/pve-manager/images/logo-128.png~ \
/usr/share/pve-patch/images/logo-128.png && \
cp -f /usr/share/pve-manager/images/proxmox_logo.png~ \
/usr/share/pve-patch/images/proxmox_logo.png && \
/usr/share/pve-patch/scripts/apply.sh
```

## Test

```
vagrant up
```
