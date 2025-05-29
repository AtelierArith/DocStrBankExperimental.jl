```julia
send(c::UDPConnection, data::String, to::IP4 = "127.0.0.1":2000) -> ::Nothing
```

Sends `data` from a `UDPConnection` to any other endpoint. This is useful for  data we want to send inside of a `UDPHandler`. To respond to the current client, we could provide  the `c.ip` as `to`, but we could also use `respond!` to simplify the process. Note that this can only happen from the base thread, as well. In the future, we might have  a way to translate this data but this is not currently supported. Please try to understand that  every addition to multi-threading data-wise is not only a head-ache, but also stressful for  others who might not use it – as we are replicating it on multiple threads.

```julia
module UserTracker
using ToolipsUDP

users = Dict{IP4, String}()

main_handler = handler() do c::UDPConnection
    if contains(c.packet, " ") || c.packet == ""
        respond!(c, "please provide a name to name yourself")
        return
    end
    push!(users, get_ip4(c) => c.packet)
    # everyone gets a join message.
    [send(c, "$(c.packet) joined", user_ip) for user_ip in keys(users)]
end

export main_handler, UDP, start!
end
```
