```
send(protocol::TCPProtocol, destination::InetAddr, message::Vector{UInt8})
```

メッセージ `message` をプレーン TCP 経由で送信し、`destination` を宛先アドレスとして使用します。メッセージは任意の IO ストリームに書き込むことができる形式で提供する必要があります。

成功した場合は true を返します。
