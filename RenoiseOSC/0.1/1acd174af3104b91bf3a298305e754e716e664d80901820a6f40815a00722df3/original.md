```
sethost!(host::Union{AbstractString,Sockets.IPAddr})
```

Set the host of the Renoise OSC server. Default value is `ip"127.0.0.1"`.

!!! compat "Julia 1.3"
    Setting the host by passing an AbstractString requires at least Julia 1.3.


# Example

```jldoctest; setup=:(using Sockets: @ip_str; using RenoiseOSC: sethost!)
julia> sethost!(ip"127.0.0.1")
Sockets.InetAddr{Sockets.IPv4}(ip"127.0.0.1", 8000)
```
