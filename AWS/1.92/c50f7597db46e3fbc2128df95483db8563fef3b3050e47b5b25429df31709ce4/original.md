```
dot_aws_config(profile=nothing) -> Union{AWSCredentials, Nothing}
```

Retrieve `AWSCredentials` from the AWS CLI configuration file. The configuration file defaults to "~/.aws/config" but can be specified using the env variable  `AWS_CONFIG_FILE`. When no credentials are found for the given `profile` then the associated `source_profile` will be used to recursively look up credentials of source profiles. If still no credentials can be found then `nothing` will be returned.

# Arguments

  * `profile`: Specific profile used to get AWSCredentials, default is `nothing`
