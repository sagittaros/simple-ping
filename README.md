# Simple Ping

All this project does is to serve an API that returns 200 status to the caller.

This is useful to be used when paired with NodePort service, so that load balancer can determine healthy nodes to route to.

## Getting started

You need nix. And if you have direnv (i am using Doom emacs) and lorri, you don't need to do anything else. This is your "virtualenv" with batteries included. Haskell language server, hlint, stylish-haskell, etc.

```sh
# requirements
nix-env -iA nixpkgs.lorri
nix-env -iA nixpkgs.direnv
```

- Refer this [Makefile](./Makefile) for command usage

- Refer [k8s](./k8s) on how to deploy this on kubernetes

## Docker

https://hub.docker.com/r/sagittaros/simple-ping

```sh
docker run -p 3000:3000 simple-ping
```

## FAQs

#### Why not just let load balancer calls /healthz of the web app?

Well, imagine that you are running private cluster (mongodb, redis) that is not meant to serve web requests. Yet you need the health ping capability in order to use Health Checks for Auto Scaling instances.

https://docs.aws.amazon.com/autoscaling/ec2/userguide/healthcheck.html

![ELB](./screenshot-elb.png)

#### Is this project an overkill?

Certainly, I am learning Nix.
