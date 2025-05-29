```
sethost!(host::Union{AbstractString,Sockets.IPAddr})
```

Renoise OSCサーバーのホストを設定します。デフォルト値は `ip"127.0.0.1"` です。

!!! compat "Julia 1.3"
    AbstractStringを渡してホストを設定するには、少なくともJulia 1.3が必要です。


# 例

```jldoctest; setup=:(using Sockets: @ip_str; using RenoiseOSC: sethost!)
julia> sethost!(ip"127.0.0.1")
Sockets.InetAddr{Sockets.IPv4}(ip"127.0.0.1", 8000)
```
