```
create_group(config::AWSConfig) -> String
create_group(config::AWSConfig, log_group_name) -> String
```

Create a CloudWatch Log Group. If the log group name is not provided, one is generated using a UUID4.

Returns the log group name.
