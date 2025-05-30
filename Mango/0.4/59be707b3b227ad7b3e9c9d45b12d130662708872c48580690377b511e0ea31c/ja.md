```
send(protocol::TCPProtocol, destination::InetAddr, message::Vector{UInt8})
```

メッセージ `message` をプレーンTCPを介して送信し、`destination` を宛先アドレスとして使用します。メッセージは、任意のIOストリームに書き込むことができる形式で提供する必要があります。

成功した場合はtrueを返します。
