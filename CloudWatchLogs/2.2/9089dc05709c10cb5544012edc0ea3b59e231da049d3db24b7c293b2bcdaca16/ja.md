```
CloudWatchLogStream(config::AWSConfig, log_group_name, log_stream_name)
```

AWSのCloudWatch Log Streamへの参照を作成します。ロググループ名とログストリーム名を指定します。このコンストラクタは、ストリームの最新の[シーケンストークン](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutLogEvents.html#CWL-PutLogEvents-request-sequenceToken)を自動的に取得します。
