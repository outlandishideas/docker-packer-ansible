## Docker-packer-ansible

This image aims to provide a usable packer image with ansible slipstreamed
inside for easy utilization of Ansible Local/Remote builders!

A few notes:

* I've based off the most official Packer image, `hashicorp/packer`
* This utilizes Alpine Linux which means its more nimble ;)
* The entrypoint has been reset to the Docker default `/bin/sh/ -c` so this
  image is more standardized for things like `gitlab-runner` or other
  application.
* I'll maintain tags which specify both packer+ansible versions, although I will
  only update this as I need to for myself and my uses. Pull Requests are very
  welcome and will be responded to as quickly as possible!


#### Example

Given you bind mount a directory `ami_build` which has your packer.json
and related ansible scripts, something like this should work.

```
docker run -v /home/user/ami_build:/build -ti -e AWS_ACCESS_KEY=blah
-e AWS_SECRET_KEY=blah inanimate/packer-ansible "packer build packer.json"
```
