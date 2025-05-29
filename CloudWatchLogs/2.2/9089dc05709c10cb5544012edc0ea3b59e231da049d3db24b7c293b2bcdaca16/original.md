```
CloudWatchLogStream(config::AWSConfig, log_group_name, log_stream_name)
```

Create a reference to a CloudWatch Log Stream on AWS with the log group name and log stream name. This constructor will automatically fetch the latest [sequence token](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutLogEvents.html#CWL-PutLogEvents-request-sequenceToken) for the stream.
