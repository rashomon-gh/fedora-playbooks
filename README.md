# fedora-playbooks

Fedora post installation steps automated with ansible.

## playbooks

The repository ships a set of focused Ansible playbooks.

```bash
playbooks
├── playbook-browsers.yml
├── playbook-devtools.yml
├── playbook-flatpaks.yml
├── playbook-gaming.yml
├── playbook-media.yml
├── playbook-nvidia.yml
├── playbook-openbangla.yml
├── playbook-starter.yml
├── playbook-tailscale.yml
├── playbook-tlp.yml
└── playbook-utils.yml
```

> [!NOTE]
> If you don't need specific playbooks you can comment them out in the `playbook.yml` file.

## Usage

First install ansible via pip

```bash
sudo dnf install python3-pip python3-libdnf5 -y
pip install ansible
````

Then run the playbooks.

> [!IMPORTANT]
> Currently the `target_user` variable inside the playbook is hardcoded, 
> so you'll have to replace it with your username.

```bash
# will ask you for your password to become sudo
ansible-playbook -i localhost, --connection=local -K playbook.yml
```

## what's not covered

| Topic | Reason |
|---|---|
| CUDA Toolkit installation | Check [RPMFusion/Howto/CUDA](https://rpmfusion.org/Howto/CUDA) and [Nvidia CUDA Toolkit Downloads](https://developer.nvidia.com/cuda-downloads). Also ensure that you install a compatible gcc compiler since the system version is always ahead by a version or two. |
| Secure Boot Setup | Check [RPMFusion/Howto/Secureboot](https://rpmfusion.org/Howto/Secure%20Boot). |
| Gnome shell extensions | Install based on your preferences. |
| VPNs and other email clients | Same as above. |

> [!TIP]
> If you're using a new gen Thinkpad (e.g. P1 Gen 7 or newer), read the [OMGLinux guide](https://www.omglinux.com/boot-linux-modern-lenovo-thinkpads-bios-setting/) on how to enable secure boot for non-Microsoft operating systems in the bios.


> [!TIP]
> If you've a dual gpu laptop (iGPU+dGPU), use the following as the launcher command to run games on the dGPU: `%command% -graphicsadapter=0` if games run on iGPU by default.
