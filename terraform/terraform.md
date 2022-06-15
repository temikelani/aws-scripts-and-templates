# Terraform Cheat Sheet/Notes <a id ='top'></a>

<br>
<br>

# Contents

- [Resources](#0)
- [`terraform init`](#1)
- [`terraform plan`](#2)
- [`terraform apply`](#3)
- [`terraform destroy`](#4)
- [`terraform state`](#5)
- [`terraform workspace`](#6)
- [`terraforn import`](#7)
- [Setup Credentials](#8)
- [`terraform validate `](#9)
- [aws required providers](#10)
- [](#11)
- [](#12)
- [](#13)
- [](#14)
- [](#15)
- [](#16)
- [](#17)
- [](#18)
- [](#19)
- [](#20)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [](#)
- [refresh, console, format, output, expressions, provisioner, lookup functions, type-object, cudr subnet](#)
- [go to top](#top)

<br>
<br>
<br>

# Resources <a id='0'></a> ([go to top](#top))

- [Terraform Commands](https://www.terraform.io/cli/commands)

<br>
<br>
<br>

# `terraform init` <a id='1'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/init)

```
terraform init
```

<br>
<br>
<br>

# `terraform plan` <a id='2'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/plan)

```
Usage: terraform plan [options]
```

```
terraform plan
```

```
terraform plan -out [plan-name]
terraform plan -out=[FILENAME]
```

<br>
<br>
<br>

# `terraform apply` <a id='3'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/apply)

```
Usage: terraform apply [options] [plan file]
```

```
terraform apply
terraform apply -auto-approve
```

```
terraform apply -var-file='="./dev.tfvars"
terraform apply -var-file='="./prod.tfvars"
```

<br>
<br>
<br>

# `terraform destroy` <a id='4'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/destroy)

```
Usage: terraform destroy [options]
```

```
terraform destroy -auto-approve
```

<br>
<br>
<br>

# `terraform state` <a id='5'></a> ([go to top](#top))

- [Documentation](https://www.terraform.io/cli/commands/state/list)
- [Documentation](https://www.terraform.io/cli/commands/state/show)
- [Documentation](https://www.terraform.io/cli/commands/state/mv)
- [Documentation](https://www.terraform.io/cli/commands/state/rm)

```
Usage: terraform state list [options] [address...]
Usage: terraform state show [options] ADDRESS
Usage: terraform state mv [options] SOURCE DESTINATION
Usage: terraform state rm [options] ADDRESS...
```

```
terraform state list
terraform state list -state=path-to-state-file
terraform state list aws_instance.bar
terraform state list module.elb
terraform state list -id=sg-1234abcd
```

```
terraform state show 'packet_device.worker'
terraform state show 'module.foo.packet_device.worker'
terraform state show 'packet_device.worker[0]'
```

```
terraform state mv -state-out=../project-1/terraform.tfstate aws_vpc.main aws_vpc.my_vpc

# rename a resource
terraform state mv packet_device.worker packet_device.helper

# move resource into a module
terraform state mv packet_device.worker module.worker.packet_device.worker
terraform state mv packet_device.worker module.worker.packet_device.main
```

<br>
<br>
<br>

# `terraform workspace` <a id='6'></a> ([go to top](#top))

- [Documentation](https://www.terraform.io/cli/commands/workspace/list)
- [Documentation](https://www.terraform.io/cli/commands/workspace/select)
- [Documentation](https://www.terraform.io/cli/commands/workspace/new)
- [Documentation](https://www.terraform.io/cli/commands/workspace/delete)
- [Documentation](https://www.terraform.io/cli/commands/workspace/show)

```
Usage: terraform workspace list [DIR]
Usage: terraform workspace select NAME [DIR]
Usage: terraform workspace new [OPTIONS] NAME [DIR]
```

```
terraform workspace --help
terraform workspace list
```

```
terraform workspace new dev
terraform workspace new -state=old.terraform.tfstate example
```

```
terraform workspace select dev
terraform workspace select default
```

```
terraform workspace delete dev # delete dev workspace
```

```
resource "aws_sqs_queue" "queue" {
    name = "${terraform.workspace}-queue"
}
```

<br>
<br>
<br>

# `terraform import` <a id='7'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/import)

```
Usage: terraform import [options] ADDRESS ID
```

```
# terraform import <resource_type>.<resource_identifier> <value>
terraform import aws_vpc.example vpc-0ce9e2544b6d49d97
```

```terraform
resource "aws_vpc" "example" {
  # (resource arguments)
}
```

<br>
<br>
<br>

# Setup Credentials <a id='8'></a> ([go to top](#top))

```
export AWS_ACCESS_KEY_ID=shjakvbslavbdsvbd
export AWS_SECRET_ACCESS_KEY=hsjalbfhvsalvfsavfuasobv
terraform refresh
```

```
provider "aws" {
  shared_config_files      = ["~/.aws/conf"]
  shared_credentials_files = ["~/.aws/creds"]
  profile                  = "terraform"
}
```

<br>
<br>
<br>

# `terraform validate` <a id='9'></a> ([go to top](#top))

[Documentation](https://www.terraform.io/cli/commands/validate)

```
Usage: terraform validate [options]
```

<br>
<br>
<br>

# aws required providers <a id='10'></a> ([go to top](#top))

[Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.0"
    }
  }
}

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}
```

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

# Title <a id=''></a> ([go to top](#top))

<br>
<br>
<br>

```

```