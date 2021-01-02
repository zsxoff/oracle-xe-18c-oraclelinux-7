# Oracle XE 18c on Oracle Linux 7

## Pre-install

### Update repository

```bash
sudo /usr/bin/ol_yum_configure.sh
```

### Install delta RPM

```bash
sudo yum install -y deltarpm
```

### Install Oracle release 7 and EPEL

```bash
sudo yum install -y oracle-release-el7 oracle-epel-release-el7
```

### Install UEK

```bash
sudo yum install -y kernel-uek kernel-uek-devel
```

### Install wget

```bash
sudo yum install -y wget
```

## Install Oracle Database 18c

### Install Oracle Database 18c Preinstall

```bash
sudo yum install -y oracle-database-preinstall-18c
```

### Download and Install Oracle Database 18c

```bash
wget https://download.oracle.com/otn-pub/otn_software/db-express/oracle-database-xe-18c-1.0-1.x86_64.rpm
sudo yum localinstall -y oracle-database-xe-18c-1.0-1.x86_64.rpm
```

### Remove Oracle Database 18c RPM

```bash
rm oracle-database-xe-18c-1.0-1.x86_64.rpm
```

### Configure Oracle Database

```bash
sudo /etc/init.d/oracle-xe-18c configure
```

## Configure system

### Automating DB Instance Shutdown and Startup

```bash
sudo systemctl daemon-reload
sudo systemctl enable oracle-xe-18c
sudo systemctl start oracle-xe-18c
```

### firewalld - open port 1521 (Oracle Database 18c) and 22 (SSH)

```bash
sudo firewall-cmd --permanent --zone=public --add-port=1521/tcp
sudo firewall-cmd --permanent --zone=public --add-port=22/tcp
sudo firewall-cmd --reload
```

## License

[![License: Unlicense](https://img.shields.io/badge/License-Unlicense-green.svg?style=flat-square)](https://unlicense.org/)

This project is licensed under the terms of the [Unlicense](https://unlicense.org/) (see [LICENSE](<https://github.com/zsxoff/oracle-xe-18c-oraclelinux-7/blob/master/LICENSE>) file).
