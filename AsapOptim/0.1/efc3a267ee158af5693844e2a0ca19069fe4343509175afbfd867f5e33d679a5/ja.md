```
SpatialVariable(node::T, vector::Vector{Float64}, lowerbound::Float64, upperbound::Float64) where {T<:Asap.AbstractNode}
```

与えられたノードのために、`vector` の正規化された方向に沿った `SpatialVariable` を定義します。次のようにします：     x' = x*0 + `value` * `vector[1]`       y' = y*0 + `value` * `vector[2]`       z' = z_0 + `value` + `vector[3]`

ここで： `lowerbound` ≤ `value` ≤ `upperbound`

そして `value` は 0 に設定されます。
