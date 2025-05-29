```
aws_user_arn(aws::AWSConfig) -> String
```

Retrieve the `User ARN` from the `AWSConfig`, if not present query STS to update the `user_arn`.

# Arguments

  * `aws::AWSConfig`: AWSConfig used to retrieve the user arn
