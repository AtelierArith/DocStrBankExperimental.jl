```
verifyemail(client::PCloudClient; kwargs...)
```

メールを確認する

検証メールに送信されたアクティベーションコードであるパラメータ `code` を期待します。

有効なコードの場合、ユーザーのメールアドレスを検証し、確認されたユーザーの `email` と `userid` を返します。

コードは、現在ログインしているユーザーとは異なるユーザーのものである可能性があることに注意してください（もしあれば）。

ソース: https://docs.pcloud.com/methods/auth/verifyemail.html

# 引数

  * `code::String`: 検証メールに送信されたアクティベーションコード

# 出力

  * `email::String`: ユーザーのメール
  * `userid::Int`: ユーザーのID

# 出力例

```
{
    "result": 0,
    "email": "pcloud@pcloud.com",
    "userid": 1234
}
```
