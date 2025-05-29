```
declineshare(client::PCloudClient; kwargs...)
```

共有リクエストを拒否します。

リクエストは、diffによって報告された`sharerequestid`で識別されるか、メールから来た`code`によって識別されます。

オプションのパラメータ`block`が設定されている場合、提供者からのすべての将来の共有リクエストは自動的に拒否されます。

ソース: https://docs.pcloud.com/methods/sharing/declineshare.html

# 引数

  * `sharerequestid::Int`: 共有リクエストのID
  * `code::String`: ユーザーのメールに送信されたコード

`sharerequestid`または`code`を使用します。

# オプションの引数

  * `block::Int`: 設定されている場合、提供者からのすべての将来の共有リクエストは自動的に拒否されます。

# 出力例

```
{
    "result": 0
}
```
