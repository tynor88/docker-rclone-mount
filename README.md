# docker-rclone-mount
Docker for Rclone FUSE mount (exposable to host and other containers)

### Supported Cloud Services:
- Google Drive
- Amazon S3
- Openstack Swift / Rackspace cloud files / Memset Memstore
- Dropbox
- Google Cloud Storage
- Amazon Drive
- Microsoft One Drive
- Hubic
- Backblaze B2
- Yandex Disk
- The local filesystem

### Creating the initial config file (.rclone.conf)
```
docker exec -it Rclone-mount rclone --config="/config/.rclone.conf" config
``` 
### IMPORTANT Extra Parameters:
In order for the FUSE mount to be exposable to the host and other docker containers, these settings have to be in the Extra Parameters option in the "Advanced View" when setting up the Docker. I've already made them default in the CA template file.

```
--cap-add SYS_ADMIN --device /dev/fuse --security-opt apparmor:unconfine -v /mnt/disks/rclone_volume/:/data:shared
```
With the above settings, the FUSE will be mounted to `/mnt/disks/rclone_volume`

 
Note if you cannot see the mount inside other dockers

This container must be started BEFORE other docker containers when sharing the FUSE mount. For automatically fixing this at startup, use the great CA Docker Autostart Manager Plugin by @Squid 

 
More documentation can be found on [Unraid Forums](https://forums.unraid.net/topic/56921-support-rclone-mount-with-fuse-support-for-plexembysonarr-etc-beta/)

NOTE: Updated for Rclone v1.50.2
