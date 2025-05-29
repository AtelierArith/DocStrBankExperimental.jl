```
create_stream(config::AWSConfig, log_group_name) -> String
create_stream(config::AWSConfig, log_group_name, log_stream_name) -> String
```

指定されたロググループの下にCloudWatchログストリームを作成します。ログストリーム名が提供されていない場合は、UUID4を使用して生成されます。

ログストリーム名を返します。
