# docker-locustio
This is a Docker base image for load testing tool [locust.io](https://locust.io).

## Usage

Any requirements you have listed in your requirements.txt will be installed during the build, and locust runs locustfile.py by default!

### standalone
Build your own docker image from this image like this:

- test folder contains locust scenrio files

```
FROM tsamaya/docker-locustio

```
Then build it and run.

`$ docker build -t mylocust .`

### distributed
If you want to run in master/slave mode, specify a different file to run, etc, you can pass the appropriate flags to the container.

`$ docker run -d --name master -P mylocust -f otherlocustfile.py --host=http://foo.com --master`
`$ docker run -d --name slave --link master -f otherlocustfile.py --host=http://foo.com --slave --master-host=master`



## resources
https://github.com/christian-blades-cb/locustio-docker
https://github.com/hakobera/docker-locust
