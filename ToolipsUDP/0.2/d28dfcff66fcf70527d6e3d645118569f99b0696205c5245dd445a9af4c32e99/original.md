```julia
start!(st::Type{ServerTemplate{:UDP}}, mod::Module; ip::IP4 = "127.0.0.1":2000, threads::UnitRange{Int64} = 1:1, 
    async::Bool = true)
```

Starts a Server Module as a `ToolipsUDPServer`. `UDP` is provided as a constant from `ToolipsUDP` and is provided to start  the server as a UDPServer. If you were to call `start!` without this argument, you'd be trying to start a `Toolips`  web-server – this will result in a server with only a `default_404` route. `threads` determines how many threads to  serve the `handler`(s) with.

```julia
module MyServer
using ToolipsUDP

responder = handler() do c::UDPConnection
    data = c.packet
    println(c.packet)
end

export responder
end

using ToolipsUDP; start!(UDP, MyServer)
```

**NOTE** that with multi-threading, you will want to annotate your handler's `Connection` as an  `AbstractUDPConnection`, in order to facilitate the `IOConnection` that can actually be sent across threads.
