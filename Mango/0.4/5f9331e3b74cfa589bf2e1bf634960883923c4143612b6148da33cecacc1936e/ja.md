```
init(protocol::Protocol{T}, stop_check::Function, data_handler::Function) where {T}
```

プロトコルの内部ループを初期化します（存在する場合）。ほとんどの実装では、これは受信者ループが開始されることを意味します。受信したメッセージを処理するために、`data_handler`関数を渡すことができます `(msg, sender) -> your handling code`。

ループのライフタイムを制御するために、stop*checkを渡す必要があります (() -> boolean)。stop*checkがtrueの場合、ループは終了します。ただし、正確な動作は実装によって異なります。
