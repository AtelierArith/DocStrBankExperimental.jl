```
aws_user_arn(aws::AWSConfig) -> String
```

`AWSConfig`から`User ARN`を取得します。存在しない場合は、`user_arn`を更新するためにSTSをクエリします。

# 引数

  * `aws::AWSConfig`: ユーザーARNを取得するために使用されるAWSConfig
