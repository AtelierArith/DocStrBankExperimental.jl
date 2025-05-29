```
resetpassword(client::PCloudClient; kwargs...)
```

ユーザーのパスワードをリセットします

失ったパスワードでメールに送信された `code` をパラメータとして期待します。

ユーザーのパスワードを `newpassword` にリセットします。

新しいパスワードは、changepassword と同じチェックの対象となります。

ソース: https://docs.pcloud.com/methods/auth/resetpassword.html

# 引数

  * `code::String`: 失ったパスワードでユーザーに送信されたコード
  * `newpassword::String`: ユーザーの新しいパスワード

# 出力例

```
{
    "result": 0
}
```
