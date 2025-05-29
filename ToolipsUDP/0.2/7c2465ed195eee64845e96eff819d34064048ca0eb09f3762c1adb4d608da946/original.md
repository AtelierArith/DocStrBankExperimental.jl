```julia
send(c::Module, data::String, to::IP4 = "127.0.0.1":2000) -> ::Nothing
```

Sends a packet of data to `to` using an actively running server `Module`. This allows us to send data  from outside of the server.

```julia
module HelloWorld
using ToolipsUDP

main_handler = handler() do c::UDPConnection
    respond!(c, "hello server")
end

export main_handler, UDP, start!
end

start!(UDP, HelloWorld)

using ToolipsUDP; send(HelloWorld, "hello to another server", "127.0.0.1":8000)
```
