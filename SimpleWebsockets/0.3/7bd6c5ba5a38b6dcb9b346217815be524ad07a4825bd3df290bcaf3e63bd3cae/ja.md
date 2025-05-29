```
ping(ws::WebsocketConnection, data::Union{String, Number})
```

`data`を`ws`ピアに対するpingメッセージとして送信します。

`data`は125バイトに制限されており、この制限を超える場合は自動的に切り捨てられます。
