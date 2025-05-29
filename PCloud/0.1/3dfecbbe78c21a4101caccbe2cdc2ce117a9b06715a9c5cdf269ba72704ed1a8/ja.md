```
newsletter_unsubscribe(client::PCloudClient; kwargs...)
```

メールで送信された `code` を使用して、ユーザーがニュースレターに登録したメールアドレスから解除します。`code` が有効な場合、ユーザーのメールアドレスは解除されます。

ソース: https://docs.pcloud.com/methods/newsletter/newsletter_unsubscribe.html

# 引数

  * `code::String`: ユーザーにメールで送信されたコード

# 出力

常に `result`=0 を送信します。たとえユーザーがニュースレターに追加されていなかった場合でも、これはセキュリティ上の理由からです。

# 出力例

```
{
    result: 0
}
```
