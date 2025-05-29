```
changemail(client::PCloudClient; kwargs...)
```

現在のユーザーのメールアドレスを変更します。`code`から`newmail`を取得します。

出典: https://docs.pcloud.com/methods/auth/changemail.html

# 引数

  * `password::String`: ユーザーの現在のパスワード
  * `code::String`: メールで送信されたコード

# 出力例

```
{
    "result": 0
}
```
