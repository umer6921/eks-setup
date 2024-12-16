# Steps to install the EKS Cluster
##  Update the apt package index and install dependencies:
```
sudo apt update
sudo apt install curl unzip
```
## Download and install AWS CLI v2:
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
```
unzip awscliv2.zip
sudo ./aws/install
```
## Verify the installation:

```
aws --version
```
You should see output similar to:
```
aws-cli/2.x.x Python/3.x.x Linux/4.x.x
```

## Login to aws account 

```
aws configrue
```

## Download kubectl

```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/kubectl
```

## Apply execute permissions to the binary:

```
chmod +x ./kubectl
```

## Copy the binary to a directory in your path:
```
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```

## Ensure kubectl is installed:
```
kubectl version --short --client
```

## Download eksctl
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```

## Move the extracted binary to /usr/bin:
```
sudo mv /tmp/eksctl /usr/bin
```

## Get the version of eksctl
```
eksctl version
```

## See the options with eksctl
```
eksctl help
```

## Provision an EKS Cluster

```
eksctl create cluster --name dev --region us-east-1 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed
```


