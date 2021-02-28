# rootless-podman

Example how to configure podman rootless on Debian 11.

## Run Playbook

```
ansible-playbook -i inventory.ini playbook.yaml
```

## Test

```
testuser@debian01:~$ cat /proc/self/uid_map
         0          0 4294967295

testuser@debian01:~$ podman unshare cat /proc/self/uid_map
WARN[0000] Failed to add podman to systemd sandbox cgroup: exec: "dbus-launch": executable file not found in $PATH 
         0       1000          1
         1     100000      65536

testuser@debian01:~$ podman run -it alpine sh
WARN[0000] Failed to add podman to systemd sandbox cgroup: exec: "dbus-launch": executable file not found in $PATH 
/ # id
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
```
