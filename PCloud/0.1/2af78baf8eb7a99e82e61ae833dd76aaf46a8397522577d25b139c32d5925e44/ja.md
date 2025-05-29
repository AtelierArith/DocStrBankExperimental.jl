```
newsletter_unsubscribemail(client::PCloudClient; kwargs...)
```

指定された `mail` に、ニュースレターからの購読を解除するために使用できるコードを含むメールを送信します。

このメールはニュースレターに追加された `mail` に送信されますが、確認される必要はありません。

ソース: https://docs.pcloud.com/methods/newsletter/newsletter_unsibscribemail.html

# 引数

  * `code::String`: ユーザーに送信されるメールに含まれるコード

# 出力

常に `result`=0 を送信します。たとえメールが送信されなかった場合でも、これはセキュリティ上の理由からです。

# 出力例

```
{
    result: 0
}
```
