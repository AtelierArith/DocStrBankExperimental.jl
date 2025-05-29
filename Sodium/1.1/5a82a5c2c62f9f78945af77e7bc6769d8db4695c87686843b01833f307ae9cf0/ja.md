```
seal(message::Vector{UInt8}, publickey)
```

メッセージを `SecretBuffer` でラップしてから `seal(::SecretBuffer, publickey)` を呼び出す便利な関数です。また、メッセージベクターを消去して空にします。
