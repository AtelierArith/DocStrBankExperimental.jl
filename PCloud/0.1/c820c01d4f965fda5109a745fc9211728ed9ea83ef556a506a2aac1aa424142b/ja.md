```
newsletter_check(client::PCloudClient; kwargs...)
```

現在ログインしているユーザーがpCloudニュースレターに登録されているかどうかを確認します。

ソース: https://docs.pcloud.com/methods/newsletter/newsletter_check.html

# 出力

フィールド `subscribed` は、ユーザーがニュースレターに登録されている場合は `true` です。

フィールド `verified` は、ユーザーがすでにメールアドレスに送信されたリンクを使用してメールを確認している場合は `true` です。

# 出力例

```
{
    subscribed: true,
    verified: false,
    result: 0
}
```
