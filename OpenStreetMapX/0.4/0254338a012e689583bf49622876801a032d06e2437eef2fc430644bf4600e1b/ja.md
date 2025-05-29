```
nodes_within_range(nodes::Dict{Int,T}, loc::T, range::Float64 = Inf) where T<:(Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF})
```

位置の範囲内にあるすべてのノードを見つける
