```julia
send(data::String, to::IP4 = "127.0.0.1":2000; from::Int64 = to.port - 5, keep_open::Bool = false) -> ::Nothing/::Sockets.UDPSocket
```

`data`を現在のコンピュータのポート`from`から`IP4`の`to`に送信します。この場合、クライアントサーバーを迅速に作成し、パケットを送信し、その後サーバーをキャンセルします。送信後、このサーバーは閉じられているため、応答を受信しないことに注意してください。これは`keep_open`引数によって変更されます。

```julia
module HelloWorld
using ToolipsUDP

main_handler = handler() do c::UDPConnection
    println("new client sent us... " * c.packet)
end

export main_handler, UDP, start!
end

start!(UDP, HelloWorld, ip = "127.0.0.1":3001)

using ToolipsUDP; send("hello friend", "127.0.0.1":3001)

# output: new client sent us... hello friend
```
