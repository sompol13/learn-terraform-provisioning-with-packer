## Learn Terraform Provisioningd with Packer
Companion code repository for learning to provision Terraform instances with Packer

### What is Pakcer
Packer is HashiCorp's open-source tool for creating machine images from source configuration. You can configure Packer images with an operating system and software for your specific use-case.

> Warning: Never pass unverified scripts into your Packer images.

### Build your Packer image
The AMI is your artifact from the Packer run and is available in your AWS account in the EC2 Images section.
- `packer build image.pkr.hcl`
- <img width="1608" alt="1" src="https://user-images.githubusercontent.com/33342822/150629192-f9a2b3ed-2e57-4463-91ba-81b9d1f170d8.png">

### Deploy your Packer image with Terraform
- Open the main.tf file and navigate to the aws_instance resource. Edit the ami attribute with the AMI ID you received from your Packer build.
- `terraform init && terraform apply`

### Verify your instance
- `ssh terraform@$(terraform output -raw public_ip) -i ../tf-packer`
- `cd go/src/github.com/hashicorp/learn-go-webapp-demo`
- `go run webapp.go`
- In your web browser, navigate your instance's IP address and port 8080 to see the app you deployed.
- <img width="1608" alt="2" src="https://user-images.githubusercontent.com/33342822/150629199-1380c9a2-f74c-4a27-adf1-f660b47ecc2d.png">

### Reference
https://learn.hashicorp.com/tutorials/terraform/packer?in=terraform/provision
