```
ssh root@10.10.10.161
root@10.10.10.161's password: 
Last login: Sat Feb 11 05:05:22 2017 from c13n1t
[root@c13n2t ~]# hostname
c13n2t
[root@c13n2t ~]# hostname -i
10.10.10.161
--------------
ssh root@10.10.10.159
root@10.10.10.159's password: 
Last login: Sat Feb 11 05:06:14 2017 from c13n2t
[root@c13mt ~]# hostname
c13mt
[root@c13mt ~]# hostname -i
10.10.10.159
[root@c13mt ~]# ssh root@10.10.10.160
root@10.10.10.160's password: 
Last login: Sat Feb 11 05:09:34 2017 from c13mt
[root@c13n1t ~]# hostname
c13n1t
[root@c13n1t ~]# hostname -i
10.10.10.160
-------------------
[root@c13n2t ~]# yum repolist
Loaded plugins: fastestmirror, langpacks
centos                                                   | 3.6 kB     00:00     
gangpbs                                                  | 2.9 kB     00:00     
(1/3): centos/group_gz                                     | 155 kB   00:00     
(2/3): gangpbs/primary_db                                  |  26 kB   00:00     
(3/3): centos/primary_db                                   | 5.3 MB   00:00     
Determining fastest mirrors
repo id                              repo name                            status
centos                               centos                               9,007
gangpbs                              progang                                 35
repolist: 9,042
---------------------
[root@c13n2t ~]# yum repolist
Loaded plugins: fastestmirror, langpacks
centos                                                   | 3.6 kB     00:00     
gangpbs                                                  | 2.9 kB     00:00     
(1/3): centos/group_gz                                     | 155 kB   00:00     
(2/3): gangpbs/primary_db                                  |  26 kB   00:00     
(3/3): centos/primary_db                                   | 5.3 MB   00:00     
Determining fastest mirrors
repo id                              repo name                            status
centos                               centos                               9,007
gangpbs                              progang                                 35
repolist: 9,042
----------------
root@c13mt ~]# yum clean all
Loaded plugins: fastestmirror, langpacks
Cleaning repos: centos gangpbs
Cleaning up everything
[root@c13mt ~]# yum repolist
Loaded plugins: fastestmirror, langpacks
centos                                                   | 3.6 kB     00:00     
gangpbs                                                  | 2.9 kB     00:00     
(1/3): centos/group_gz                                     | 155 kB   00:00     
(2/3): gangpbs/primary_db                                  |  26 kB   00:00     
(3/3): centos/primary_db                                   | 5.3 MB   00:00     
Determining fastest mirrors
repo id                              repo name                            status
centos                               centos                               9,007
gangpbs                              progang                                 35
repolist: 9,042
----------
[root@c13n1t ~]# systemctl status autofs
● autofs.service - Automounts filesystems on demand
   Loaded: loaded (/usr/lib/systemd/system/autofs.service; enabled; vendor preset: disabled)
   Active: active (running) since Sat 2017-02-11 06:14:27 IST; 38s ago
 Main PID: 21153 (automount)
   CGroup: /system.slice/autofs.service
           └─21153 /usr/sbin/automount --pid-file /run/autofs.pid

Feb 11 06:14:27 c13n1t systemd[1]: Starting Automounts filesystems on demand...
Feb 11 06:14:27 c13n1t systemd[1]: Started Automounts filesystems on demand.
Hint: Some lines were ellipsized, use -l to show in full.
-------------
[root@c13n2t ~]# systemctl status autofs
● autofs.service - Automounts filesystems on demand
   Loaded: loaded (/usr/lib/systemd/system/autofs.service; enabled; vendor preset: disabled)
   Active: active (running) since Sat 2017-02-11 06:13:04 IST; 3min 3s ago
 Main PID: 20898 (automount)
   CGroup: /system.slice/autofs.service
           └─20898 /usr/sbin/automount --pid-file /run/autofs.pid

Feb 11 06:13:04 c13n2t systemd[1]: Starting Automounts filesystems on demand...
Feb 11 06:13:04 c13n2t systemd[1]: Started Automounts filesystems on demand.
Hint: Some lines were ellipsized, use -l to show in full.
----------------
[root@c13n1t ~]# cd /apps
[root@c13n1t apps]# df -h
Filesystem          Size  Used Avail Use% Mounted on
/dev/sda2            99G  3.7G   90G   4% /
devtmpfs            2.0G     0  2.0G   0% /dev
tmpfs               2.0G     0  2.0G   0% /dev/shm
tmpfs               2.0G  8.9M  2.0G   1% /run
tmpfs               2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda1           976M  115M  794M  13% /boot
tmpfs               396M     0  396M   0% /run/user/0
10.10.10.159:/apps   99G  3.7G   90G   4% /nfsroot/apps
----------------------------
[root@c13n2t ~]# cd /apps
[root@c13n2t apps]# df -h
Filesystem          Size  Used Avail Use% Mounted on
/dev/sda2            99G  3.7G   90G   4% /
devtmpfs            2.0G     0  2.0G   0% /dev
tmpfs               2.0G     0  2.0G   0% /dev/shm
tmpfs               2.0G  8.9M  2.0G   1% /run
tmpfs               2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda1           976M  115M  794M  13% /boot
tmpfs               396M     0  396M   0% /run/user/0
10.10.10.159:/apps   99G  3.7G   90G   4% /nfsroot/apps
---------------
[root@c13n1t ~]# id c13mt
uid=1000(c13mt) gid=1000(c13mt) groups=1000(c13mt)
----------------
root@c13n2t ~]# ssh c13mt
The authenticity of host 'c13mt (10.10.10.159)' can't be established.
ECDSA key fingerprint is 6c:cc:04:2e:64:6e:57:9d:8f:6f:7e:b9:9f:6e:0f:7b.
Are you sure you want to continue connecting (yes/no)? yes 
Warning: Permanently added 'c13mt' (ECDSA) to the list of known hosts.
root@c13mt's password: 
Last failed login: Sat Feb 11 06:37:37 IST 2017 from c13n1t on ssh:notty
There was 1 failed login attempt since the last successful login.
Last login: Sat Feb 11 05:47:07 2017 from c13n2t
-------------------------------
[c13mt@c13n1t ~]$ cd .ssh
[c13mt@c13n1t .ssh]$ cat id_rsa.pub > authorized_keys
[c13mt@c13n1t .ssh]$ chmod 600 authorized_keys
[c13mt@c13n1t .ssh]$ ssh c13n1t
Last login: Sat Feb 11 06:46:03 2017
[c13mt@c13n1t ~]$ logout
Connection to c13n1t closed.
[c13mt@c13n1t .ssh]$ exit
logout
[root@c13n1t ~]# exit
logout
Connection to c13n1t closed.
[root@c13mt ~]# su - c13mt
Last login: Sat Feb 11 06:42:54 IST 2017 on pts/9
[c13mt@c13mt ~]$ ssh c13n1t
Last login: Sat Feb 11 06:47:43 2017 from c13n1t
```









