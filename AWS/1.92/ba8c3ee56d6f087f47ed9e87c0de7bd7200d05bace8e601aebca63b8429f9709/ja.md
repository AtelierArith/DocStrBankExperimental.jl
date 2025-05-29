```
check_credentials(
    aws_creds::AWSCredentials, force_refresh::Bool=false
) -> AWSCredentials
```

現在のAWSCredentialsをチェックし、期限が近い場合はそれを更新します。`force_refresh`が`true`の場合、資格情報は即座に更新されます。

# 引数

  * `aws_creds::AWSCredentials`: チェックまたは更新されるAWSCredentials

# キーワード

  * `force_refresh::Bool=false`: 資格情報を更新するには`true`を指定

# 例外

  * `error("Can't find AWS credentials!")`: 資格情報が見つからない場合
