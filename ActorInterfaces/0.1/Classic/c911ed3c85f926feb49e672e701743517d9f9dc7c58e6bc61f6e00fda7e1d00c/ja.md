```
send(recipient::Addr, msg, [ctx])
```

メッセージ `msg` を `recipient` アクターアドレスに送信します。

ctx 引数は [`@ctx`](@ref) によって自動的に注入されることがあります。
