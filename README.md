Playbook for Go workplace in CentOS
====

Simplest Go workplace in CentOS

## Description

You can create Go workplace (bin, src, pkg). 
By default, Go 1.9.4 will be installed.


## Requirement

CentOS  
2.0 or later Ansible is required.

## Install

```
git clone https://github.com/tomocy/ansible_go.git
```

## Usage

Edit file 'hosts' for your configuration  
```rb:hosts
[remotes]
XXX.XXX.XX.XX # Host
ansible_ssh_user=YYY # SSH user
ansible_ssh_private_key_file=ZZZ # Path to SSH private key
```

If you want to use other Go version,  
find it at https://golang.org/dl/ and copy File name and SHA256 Checksum of Linux  
Edit 'vars/main.yml'
```rb:main.yml
go_version_target: "go version goX.X.X linux/YYY" # X.X.X is Go version. YYY is architecture.
go_tarball: "FILENAME" # File name you copied
go_download_url: "https://storage.googleapis.com/golang/{{ go_tarball }}"
go_tarball_checksum: "sha256:CHECKSUM" # Checksum you copied
set_go_path: true
```

Last, command this at the directory you cloned
```
ansible-playbook -i hosts site.yml
```


## Author

[tomocy](https://github.com/tomocy)
