```
newsletter_subscribe(client::PCloudClient; kwargs...)
```

pCloudニュースレターにメールを登録します。

メールがまだ確認されていない場合、リンクがメールで送信されます。リンクを使用した後、メールの所有者は自分のメールを確認します。

ソース: https://docs.pcloud.com/methods/newsletter/newsletter_subscribe.html

# 引数

  * `mail::String`: ニュースレターリストに入力されたメール

# 出力

フィールド `verifymail` は、確認メールが送信された場合に `true` になります。

# 出力例

```
{
    verifymail: true,
    result: 0
}
```
