```
lostpassword(client::PCloudClient; kwargs...)
```

現在のユーザーのパスワードを変更します

ユーザーの `mail` をパラメータとして受け取り、このメールアドレスに指示とユーザーのパスワードをリセットするためのリンクを送信します。

セキュリティ上の理由から、`mail` に対応するシステムのユーザーが存在しなくても、成功した返信が送信されます。

ソース: https://docs.pcloud.com/methods/auth/lostpassword.html

# 引数

  * `mail::String`: 指示が送信されるユーザーのメールアドレス

# 出力例

```
{
    "result": 0
}
```
