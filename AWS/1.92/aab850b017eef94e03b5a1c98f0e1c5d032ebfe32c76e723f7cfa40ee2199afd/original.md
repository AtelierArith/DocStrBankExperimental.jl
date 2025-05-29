```
dot_aws_credentials(profile=nothing) -> Union{AWSCredentials, Nothing}
```

Retrieve `AWSCredentials` from the AWS CLI credentials file. The credential file defaults to "~/.aws/credentials" but can be specified using the env variable `AWS_SHARED_CREDENTIALS_FILE`.

# Arguments

  * `profile`: Specific profile used to get AWSCredentials, default is `nothing`
