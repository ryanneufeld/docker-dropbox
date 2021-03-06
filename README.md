About this container
---
[![Docker Build Status](https://img.shields.io/docker/build/cturra/dropbox.svg)](https://hub.docker.com/r/cturra/dropbox/)
[![Docker Pulls](https://img.shields.io/docker/pulls/cturra/dropbox.svg)](https://hub.docker.com/r/cturra/dropbox/)
[![Apache licensed](https://img.shields.io/badge/license-Apache-blue.svg)](https://raw.githubusercontent.com/cturra/docker-dropbox/badges/LICENSE)

This container runs the Dropbox Linux client. More about Dropbox can be found at:

  https://www.dropbox.com


Running from Docker Hub
---
Pull and run -- it's this simple.

```
# pull from docker hub
$> docker pull cturra/dropbox

# run docker
$> docker run --name=dropbox                     \
              --restart=always                   \
              --detach=true                      \
              --memory=512m                      \
              --net=host                         \
              --volume=/data/dropbox:/dropbox:rw \
              cturra/dropbox
```


Building and Running with Docker engine
---
Using the `vars` file in this git repo, you can update any of the variables to
reflect your environment. Once updated, simply execute the `build` then `run` scripts.

```
# build docker
$> ./build.sh

# run docker
$> ./run.sh
```


Help
---
The first time you run this, you'll need to link the container to your dropbox
account. If you check out the supervisor logs, located within your volume mount
(from the example above that would be `/data/dropbox/logs/`) you should see a
message like:

```
This computer isn't linked to any Dropbox account...
Please visit https://www.dropbox.com/cli_link_nonce?nonce=90084227dc5340d88136f436c5be18fb
to link this device.
```

Simply copy that link into your browser and complete the linking process. After
you've done this the first time, subsequent runs shouldn't prompt you for this.

Note that the container expects /dropbox to look like this:

```
├── dropbox
│   ├── Dropbox [ If you have a pre-existing Dropbox directory, you can move it here. ]
│   └── logs
│       └── supervisor
```

You can use the following command as an example to create this structure:

```
mkdir -p /data/dropbox/Dropbox
mkdir -p /data/dropbox/logs/supervisor
```
