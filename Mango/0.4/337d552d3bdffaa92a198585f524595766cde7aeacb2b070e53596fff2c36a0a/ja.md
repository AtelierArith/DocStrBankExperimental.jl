```
send(protocol::Protocol{T}, destination::T, message::Any) where {T}
```

メッセージ `message` をアドレス `destination` で知られているエージェントに送信します。メッセージがどのように処理されるかは、呼び出されるプロトコルによって決まります。

宛先の型はプロトコルと一致する必要があります。この関数は、メッセージが正常に送信されたかどうかを示すブール値を返します。
