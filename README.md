# RUNNING `docker` WITHOUT USING `sudo`

The Docker daemon binds to a Unix socket, not a TCP port. By default it's the root user that owns the Unix socket, and other users can only access it using sudo. The Docker daemon always runs as the root user.

If you don't want to preface the docker command with sudo, create a Unix group called docker and add users to it. When the Docker daemon starts, it creates a Unix socket accessible by members of the docker group.

Create a group named docker:

`sudo groupadd docker`

Adding your user name to the group:

`sudo usermod -aG docker $USER`

You can restart your computer or you can type the below for activate the changes:

`newgrp docker`

Now you can use `docker` without `sudo`.
