```
aws_get_region(; profile=nothing, config=nothing, default="us-east-1")
```

AWSリクエストに使用すべき現在のAWSリージョンを決定します。優先順位の順序は、[AWS CLIで使用されるもの](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-precedence)と同じです：

1. 環境変数：`AWS_DEFAULT_REGION`環境変数で指定されたもの。
2. AWS設定ファイル：設定ファイル内の`profile`で指定された`region`、通常は"~/.aws/config"。
3. IAMロールが設定されたAmazon EC2インスタンスのインスタンスメタデータサービス
4. デフォルトリージョン：指定された`default`を使用、通常は"us-east-1"。

# キーワード

  * `profile`：AWS設定プロファイルの名前（ある場合）。デフォルトは`nothing`で、`AWS._aws_get_profile()`を使用することにフォールバックします。
  * `config`：`Inifile`としてロードされたAWS設定または設定ファイルへのパス。デフォルトは`nothing`で、`dot_aws_config_file()`を使用することにフォールバックします。
  * `default`：高い優先順位が見つからなかった場合に返すリージョン。現在のAWSリージョンが定義されていないことを知りたい場合は、これを`nothing`に設定するのが便利です。
