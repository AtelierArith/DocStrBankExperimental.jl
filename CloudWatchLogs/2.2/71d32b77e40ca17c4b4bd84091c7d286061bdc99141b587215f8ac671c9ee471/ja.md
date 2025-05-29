```
create_group(config::AWSConfig) -> String
create_group(config::AWSConfig, log_group_name) -> String
```

CloudWatchロググループを作成します。ロググループ名が指定されていない場合は、UUID4を使用して生成されます。

ロググループ名を返します。
