```
aws_account_number(aws::AWSConfig) -> String
```

`AWSConfig`から`AWSアカウント番号`を取得します。存在しない場合は、STSをクエリして`AWSアカウント番号`を更新します。

# 引数

  * `aws::AWSConfig`: AWSアカウント番号を取得するために使用されるAWSConfig
