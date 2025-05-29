```
IPv6Net(str::AbstractString)
IPv6Net(ip::IPv6, netmask::Int)

IPv6ネットワークを表す型。

# 例

```

julia julia> IPv6Net("1::2/64") IPv6Net("1::/64")

julia> IPv6Net(ip"1::2", 64) IPv6Net("1::/64") ```
