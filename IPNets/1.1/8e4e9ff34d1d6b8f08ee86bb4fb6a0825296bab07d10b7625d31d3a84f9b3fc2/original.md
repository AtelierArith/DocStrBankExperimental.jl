```
IPv6Net(str::AbstractString)
IPv6Net(ip::IPv6, netmask::Int)
```

Type representing a IPv6 network.

# Examples

```julia
julia> IPv6Net("1::2/64")
IPv6Net("1::/64")

julia> IPv6Net(ip"1::2", 64)
IPv6Net("1::/64")
```
