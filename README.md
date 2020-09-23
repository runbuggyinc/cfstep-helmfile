# cfstep-helmfile [![Codefresh build status]( https://g.codefresh.io/api/badges/pipeline/codefresh-inc/steps%2Fhelmfile?branch=master&key=eyJhbGciOiJIUzI1NiJ9.NTY3MmQ4ZGViNjcyNGI2ZTM1OWFkZjYy.AN2wExsAsq7FseTbVxxWls8muNx_bBUnQWQVS8IgDTI&type=cf-1)]( https%3A%2F%2Fg.codefresh.io%2Fpipelines%2Fhelmfile%2Fbuilds%3FrepoOwner%3Dcodefresh-contrib%26repoName%3Dcfstep-helmfile%26serviceName%3Dcodefresh-contrib%252Fcfstep-helmfile%26filter%3Dtrigger%3Abuild~Build%3Bbranch%3Amaster%3Bpipeline%3A5e8b61b07c985c3e9651b7f3~helmfile)

Codefresh Step for helmfile

This step utilizes Codefresh helm Docker image and wraps helmfile around that image.

Helmfile: https://github.com/roboll/helmfile

### Steps to Build an Image for a Helmfile Specific Version
Run the following commands to build a Codefresh Helmfile docker image:  
1. Clone this git repository with the command:
	```console
	git clone git@github.com:runbuggyinc/cfstep-helmfile.git
	```
2. Go to the created directory:
 	```console
	cd cfstep-helmfile
	```
3. Build the docker image, adding the versions you need in the parameters. Example:
	```console
	docker build -t runbuggy/cfstep-helmfile:2.14.3-0.125.5 --build-arg HELM_VERSION=2.14.3 --build-arg HELM_DIFF_VERSION=3.1.2 --build-arg HELM_SECRETS_VERSION=2.0.2 --build-arg HELMFILE_VERSION=0.125.5 . > pepe 2>&1
	```
4. Run `docker images` to find out the IMAGE ID of the image created in the step before.
5. Tag the image with the AWS Docker repository and bucket with the following command:
	```console
	docker tag 213e8f1e08a6 236900137235.dkr.ecr.us-west-2.amazonaws.com/runbuggy/cfstep-helmfile:2.14.3-0.125.5
	```
6. Push image to AWS Docker repository with the following command:
	```console
	docker push 236900137235.dkr.ecr.us-west-2.amazonaws.com/runbuggy/cfstep-helmfile:2.14.3-0.125.5. 
	```
	Note: You might need to re-authenticate with AWS from you local machine with the following command:
	
	```console
	aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 236900137235.dkr.ecr.us-west-2.amazonaws.com
	```
	
	
