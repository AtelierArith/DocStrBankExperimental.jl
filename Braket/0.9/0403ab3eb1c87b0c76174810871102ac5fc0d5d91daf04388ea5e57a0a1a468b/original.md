```
AwsDevice(device_arn::String; config::AWSConfig=global_aws_config()) -> AwsDevice
```

Encapsulates an AWS managed device with arn `device_arn` and refreshes its metadata (see [`refresh_metadata!](@ref)) right away.
