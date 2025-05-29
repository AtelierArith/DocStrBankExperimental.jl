```julia
send(data::String, to::IP4 = "127.0.0.1":2000; from::Int64 = to.port - 5, keep_open::Bool = false) -> ::Nothing/::Sockets.UDPSocket
```

Sends `data` to the `IP4` `to` from the port `from` on the current computer. In this case, we will  quickly create a client server, send the packet, and then cancel the server. Note that that after sending  this server will not receive responses, as it is closed. This changes with the `keep_open` argument.

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
