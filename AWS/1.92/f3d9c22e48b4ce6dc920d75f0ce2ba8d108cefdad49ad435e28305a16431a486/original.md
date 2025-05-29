```
aws_get_region(; profile=nothing, config=nothing, default="us-east-1")
```

Determine the current AWS region that should be used for AWS requests. The order of precedence mirrors what is [used by the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-precedence):

1. Environmental variable: as specified by the `AWS_DEFAULT_REGION` environmental variable.
2. AWS configuration file: `region` as specified by the `profile` in the configuration file, typically "~/.aws/config".
3. Instance metadata service on an Amazon EC2 instance that has an IAM role configured
4. Default region: use the specified `default`, typically "us-east-1".

# Keywords

  * `profile`: Name of the AWS configuration profile, if any. Defaults to `nothing` which falls back to using `AWS._aws_get_profile()`
  * `config`: AWS configuration loaded as an `Inifile` or a path to a configuration file. Defaults to `nothing` which falls back to using `dot_aws_config_file()`
  * `default`: The region to return if no high-precedence was found. Can be useful to set this to `nothing` if you want to know that no current AWS region was defined.
