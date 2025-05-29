```
IPv4Net(str::AbstractString)
IPv4Net(ip::IPv4, netmask::Int)
IPv4Net(ip::IPv4, netmask::IPv4)
```

IPv4ネットワークを表す型。

# 例

```julia
julia> IPv4Net("192.168.0.0/24")
IPv4Net("192.168.0.0/24")

julia> IPv4Net(ip"192.168.0.0", 24)
IPv4Net("192.168.0.0/24")

julia> IPv4Net(ip"192.168.0.0", ip"255.255.255.0")
IPv4Net("192.168.0.0/24")
```
