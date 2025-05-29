```julia
get_ip4(c::UDPConnection) -> ::Toolips.IP4
```

A `get_ip` equivalent for the `Toolips.IP4` data-type, which holds both the      port and the IP address. This is provided exclusively by `ToolipsUDP` because the port  with a `Toolips` HTTP server in production will always be 80 unless an absurdly specific case.

```julia
    default_handler = handler() do c::UDPConnection
    println("served a client")
    respond!(c, "hello world!")
end
```
