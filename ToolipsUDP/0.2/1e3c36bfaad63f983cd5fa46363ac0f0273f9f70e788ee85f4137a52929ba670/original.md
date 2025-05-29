```julia
respond!(c::AbstractUDPConnection, data::String) -> ::Nothing
```

The quintessential way to return data to a client; `respond!` takes the place of  `write!` in conventional `Toolips`, allowing us to write data directly onto an incoming  packet.

```julia
module HelloWorld
using ToolipsUDP


main_handler = handler() do c::UDPConnection
    respond!(c, "hello world!")
end

export main_handler
end

# a multi-handler can also be passed a `Function` to automatically make the main handler.
multi_handler = MultiHandler() do c::AbstractUDPConnection

end
```
