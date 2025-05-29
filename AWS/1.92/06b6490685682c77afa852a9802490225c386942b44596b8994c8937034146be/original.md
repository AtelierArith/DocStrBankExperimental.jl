```
aws_account_number(aws::AWSConfig) -> String
```

Retrieve the `AWS account number` from the `AWSConfig`, if not present query STS to update the `AWS account number`.

# Arguments

  * `aws::AWSConfig`: AWSConfig used to retrieve the AWS account number
