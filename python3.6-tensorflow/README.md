Tensorflow Docker images compiled with CPU-optimizations.

# Building and running

## CPU (no GPU)

```bash
docker run --rm -i --tty triage/python3.6-tensorflow:latest python -c "from tensorflow.python.client import device_lib; print(device_lib.list_local_devices())"
```

```
$ docker run --rm -i --tty triage/python3.6-tensorflow:latest python -c "import tensorflow; from tensorflow.python.client import device_lib; print(device_lib.list_local_devices())"
[name: "/cpu:0"
device_type: "CPU"
memory_limit: 268435456
locality {
}
incarnation: 5043280336973552040
]
```

----

Setting up Docker on a new Ubuntu 16.04 Xenial environment:

```bash
#!/usr/bin/env bash
sudo apt-get -y install dirmngr software-properties-common apt-transport-https
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
sudo apt-add-repository 'deb https://apt.dockerproject.org/repo ubuntu-xenial main'
sudo apt-get -y update
apt-cache policy docker-engine
sudo apt-get install -y docker-engine

sudo usermod -aG docker $USER
#sudo su - $USER
```

Exit and start a new shell for Docker permissions.