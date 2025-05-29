```
dot_aws_credentials(profile=nothing) -> Union{AWSCredentials, Nothing}
```

AWS CLIの認証ファイルから`AWSCredentials`を取得します。認証ファイルのデフォルトは"~/.aws/credentials"ですが、環境変数`AWS_SHARED_CREDENTIALS_FILE`を使用して指定することができます。

# 引数

  * `profile`: `AWSCredentials`を取得するために使用される特定のプロファイル、デフォルトは`nothing`です。
