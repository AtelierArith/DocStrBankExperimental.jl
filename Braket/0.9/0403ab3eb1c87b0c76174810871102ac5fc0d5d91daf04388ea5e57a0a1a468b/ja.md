```
AwsDevice(device_arn::String; config::AWSConfig=global_aws_config()) -> AwsDevice
```

arn `device_arn` を持つAWS管理デバイスをカプセル化し、すぐにそのメタデータを更新します（[`refresh_metadata!](@ref)`を参照）。
