```julia
remove_handler!(c::UDPConnection) -> ::Nothing
```

Removes a currently selected `NamedHandler`, returning the client  to the `main_handler` provided to the `MultiHandler`.

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
    remove_hanlder!(c)
end

multi_handler = ToolipsUDP.MultiHandler(main_handler)

export multi_handler, start!, UDP
export main_handler, second_step
end

# this server will continuously switch between response 1 and response 2.
```
