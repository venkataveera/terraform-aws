# AWS: Creating Windows and Linux Infrastructure using Terraform

<!-- TOC -->

- [Development Environment Setup](#development-environment-setup)
- [Create Windows EC2 Instance](#create-windows-ec2-instance)
- [Create Linux EC2 Instance](#create-linux-ec2-instance)
- [Cleanup the resources](#cleanup-the-resources)

<!-- /TOC -->

### Development Environment Setup
- Install the [Terraform CLI](https://learn.hashicorp.com/tutorials/terraform/install-cli) 
- Install the [AWS CLI](https://aws.amazon.com/cli/)

### Create Windows EC2 Instance
- Clone this repo to a folder
- Open a command prompt and navigate to repo folder i.e. terraform-aws\windows
- Run `aws configure` to configure to AWS CLI
    ```
        $ aws configure
        AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
        AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
        Default region name [None]: us-east-1
        Default output format [None]: json
    ```

- Initialize the `Terraform` using below command, this will install the required plugins to current folder
	```
	$ terraform init
	```
    Output:
    ```
        Initializing the backend...

        Initializing provider plugins...
        - Checking for available provider plugins...
        - Downloading plugin for provider "aws" (hashicorp/aws) 3.5.0...

        * provider.aws: version = "~> 3.5"

        Terraform has been successfully initialized!

        You may now begin working with Terraform. Try running "terraform plan" to see
        any changes that are required for your infrastructure. All Terraform commands
        should now work.
    ```
- Run `Terraform Plan` to see what resources will be created

	```
	$ terraform plan
	```
    Output:
    ```
        Terraform will perform the following actions:

        # aws_instance.windows_instance[0] will be created
        + resource "aws_instance" "windows_instance" {
            ...............
            ...............

        # aws_vpc.default will be created
        + resource "aws_vpc" "default" {
            ...............
            ...............

        ...............
        ...............

        Plan: 7 to add, 0 to change, 0 to destroy.

        ------------------------------------------------------------------------

    ```

- If plan looks good, then run `Terraform Apply` to create infrastructure

	```
	$ terraform apply
	```
    Output:
    ```
        Terraform will perform the following actions:

        # aws_instance.windows_instance[0] will be created
        + resource "aws_instance" "windows_instance" {
            ...............
            ...............

        # aws_vpc.default will be created
        + resource "aws_vpc" "default" {
            ...............
            ...............

        ...............
        ...............

        Apply complete! Resources: 7 added, 0 changed, 0 destroyed.
    ```

### Create Linux EC2 Instance
- Clone this repo to a folder
- Open command prompt and navigate to repo folder i.e. terraform-aws\linux
- Run `aws configure` to configure to AWS CLI
    ```
        $ aws configure
        AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
        AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
        Default region name [None]: us-east-1
        Default output format [None]: json
    ```

- Repeat above `terraform` steps outlined (for windows) to create a Linux EC2 Instance


### Cleanup the resources
- Once you complete verifying and working with EC2 Instances
- Run `Terraform Destroy` to delete the resources from AWS

	```
	$ terraform destroy
	```
    Output:
    ```
        Terraform will perform the following actions:

        # aws_instance.windows_instance[0] will be created
        + resource "aws_instance" "windows_instance" {
            ...............
            ...............

        # aws_vpc.default will be created
        + resource "aws_vpc" "default" {
            ...............
            ...............

        ...............
        ...............

        Destroy complete! Resources: 7 destroyed.
    ```