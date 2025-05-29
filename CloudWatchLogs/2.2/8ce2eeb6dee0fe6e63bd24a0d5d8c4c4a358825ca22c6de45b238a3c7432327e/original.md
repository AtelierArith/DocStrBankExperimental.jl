```
create_stream(config::AWSConfig, log_group_name) -> String
create_stream(config::AWSConfig, log_group_name, log_stream_name) -> String
```

Create a CloudWatch Log Stream under a given Log Group. If the log stream name is not provided, one is generated using a UUID4.

Returns the log stream name.
