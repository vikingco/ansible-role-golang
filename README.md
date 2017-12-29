# Ansible Role: Golang

An ansible role that installs Golang on Linux

## Requirements

None.

## Role Variables

Available variables are listed below (`defaults/main.yml`)

    go_version: 1.9.2
    go_checksum: de874549d9a8d8d8062be05808509c09a88a248e77ec14eb77453530829ac02b

This is the go version you would like to install. The default version is 1.9.2 and the default platform is Linux/amd64. The default checksum corresponds to the download for the default version on the default platform.

    go_install_directory: /usr/local/go

The default installation directory is `/usr/local/go`. You can override this variable to `/opt/go` or anything else.

    go_tar_archive_location: /tmp/go{{ go_version }}.tar.gz

This is where the go tarball is downloaded to.

    go_download_url: "https://storage.googleapis.com/golang/\
      go{{ go_version }}.{{ ansible_system|lower }}-{{ arch_mapping[ansible_architecture]|default(ansible_architecture) }}.tar.gz"

This is the download url that is assembled from the variables listed above. You can change this variable, but it's not advised because there are tasks that depend on other variables like `go_version` which decide whether to download a new tarball.
