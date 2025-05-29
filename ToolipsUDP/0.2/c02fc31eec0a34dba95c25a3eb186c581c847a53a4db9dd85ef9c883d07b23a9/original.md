```julia
set_handler!(c::UDPConnection, args ...) -> ::Nothing
```

Sets a `NamedHandler` for a `MultiHandler` for the client      currently being served by `c`.

```julia
# for current client
set_handler!(c::UDPConnection, name::String)
# for other clients
set_handler!(c::UDPConnection, ip4::IP4, name::String)
```

```example
module HandlerSample
using ToolipsUDP


main_handler = handler() do c::UDPConnection
    println("response 1")
    set_handler!(c, "second")
end

second_step = handler("second") do c::UDPConnection
    println("response 2")
    respond!(c, "you made it to the second screen!")
end

multi_handler = ToolipsUDP.MultiHandler(main_handler)

export multi_handler, start!, UDP
export main_handler, second_step
end
```
