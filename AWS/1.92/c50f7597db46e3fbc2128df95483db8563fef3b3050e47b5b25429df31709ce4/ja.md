```
dot_aws_config(profile=nothing) -> Union{AWSCredentials, Nothing}
```

AWS CLI 設定ファイルから `AWSCredentials` を取得します。設定ファイルのデフォルトは "~/.aws/config" ですが、環境変数 `AWS_CONFIG_FILE` を使用して指定することもできます。指定された `profile` に対して資格情報が見つからない場合は、関連する `source_profile` を使用して、ソースプロファイルの資格情報を再帰的に検索します。それでも資格情報が見つからない場合は `nothing` が返されます。

# 引数

  * `profile`: `AWSCredentials` を取得するために使用される特定のプロファイル、デフォルトは `nothing` です。
