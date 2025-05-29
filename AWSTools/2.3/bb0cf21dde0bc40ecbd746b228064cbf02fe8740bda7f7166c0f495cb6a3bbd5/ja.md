```
assume_role(role_arn, [role_session_name]) -> AWSConfig
```

新しいロールを引き受けることによって新しい `AWSConfig` を生成します。引き受けたロールを使用するには、実行するさまざまなAWS呼び出しでこの設定を使用する必要があります。

# 引数

  * `role_arn::AbstractString`: 引き受けるロールのARN。
  * `role_session_name::AbstractString`: セッション名の一意の識別子であるオプションの文字列。

# キーワード

  * `config::AWSConfig`: ロールを引き受ける際に使用するAWS設定。
