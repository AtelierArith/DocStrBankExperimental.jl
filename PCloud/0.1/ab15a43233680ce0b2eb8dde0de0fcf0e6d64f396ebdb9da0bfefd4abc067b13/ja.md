```
sendchangemail(client::PCloudClient; kwargs...)
```

ログインしているユーザーにリンク付きのメールを送信します。

`newmail` と `code` を送信すると、`newmail` に最後のステップへのリンクを含むメールが送信されます。

ソース: https://docs.pcloud.com/methods/auth/sendchangemail.html

# オプション引数

  * `newmail::String`: ユーザーの新しいメールアドレス
  * `code::String`: メールに送信されたコード

# 出力例

```
{
    "result": 0
}
```
