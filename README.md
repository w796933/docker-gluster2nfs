# docker-gluster2nfs
[![](https://images.microbadger.com/badges/image/fabriziogaliano/gluster2nfs.svg)](https://microbadger.com/images/fabriziogaliano/gluster2nfs "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/fabriziogaliano/gluster2nfs.svg)](https://microbadger.com/images/fabriziogaliano/gluster2nfs "Get your own version badge on microbadger.com")

This Docker container allow mounting and access through NFS on multiple Gluster Volumes

## Quick start

# Run gluster2nfs on Gluster host

```
docker run -d -p 2049:2049 --privileged fabriziogaliano/gluster2nfs
```

## Example Docker-Compose file (Strongly adviced)

```
version: '2'
services:
    glusterfns:
       image: fabriziogaliano/docker-gluster2nfs:latest

       container_name: gluster2nfs

       privileged: true

       environment:
          GLUSTER_VOLUMES: 'vol01 vol02'
          GLUSTER_HOST: glusterhost01.local.domain

       extra_hosts:
          - glusterhost01.local.domain:192.168.0.5
          - glusterhost02.local.domain:192.168.0.10

       ports:
          - "2049:2049"

       restart: always
```
