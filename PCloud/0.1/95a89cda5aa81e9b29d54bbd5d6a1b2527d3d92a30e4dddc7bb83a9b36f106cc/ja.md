```
newsletter_verifyemail(client::PCloudClient; kwargs...)
```

ユーザーがニュースレターに登録したメールアドレスに送信された `code` を使用します。 `code` が有効な場合、ユーザーのメールアドレスは確認済みとしてマークされます。

ソース: https://docs.pcloud.com/methods/newsletter/newsletter_verifyemail.html

# 引数

  * `code::String`: ユーザーに送信されたメールのコード

# 出力

確認済みとしてマークされた `email` が設定されます。これはセキュリティ上の理由からです。

# 出力例

```
{
    result: 0,
    email: "newsletter@pcloud.com"
}
```
