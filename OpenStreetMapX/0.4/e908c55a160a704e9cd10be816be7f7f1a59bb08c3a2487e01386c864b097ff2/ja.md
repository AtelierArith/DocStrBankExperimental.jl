```
nearest_node(nodes::Dict{Int,T}, loc::T) where T<:(Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF})
```

指定された位置 `loc` に最も近いノードを見つけます。
