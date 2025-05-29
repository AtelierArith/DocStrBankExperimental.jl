```
IPv4Net(str::AbstractString)
IPv4Net(ip::IPv4, netmask::Int)
IPv4Net(ip::IPv4, netmask::IPv4)
```

Type representing a IPv4 network.

# Examples

```julia
julia> IPv4Net("192.168.0.0/24")
IPv4Net("192.168.0.0/24")

julia> IPv4Net(ip"192.168.0.0", 24)
IPv4Net("192.168.0.0/24")

julia> IPv4Net(ip"192.168.0.0", ip"255.255.255.0")
IPv4Net("192.168.0.0/24")
```
