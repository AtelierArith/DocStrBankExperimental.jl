```
SpatialVariable(node::T, lowerbound::Float64, upperbound::Float64, axis::Symbol = :Z) where {T<:Asap.AbstractNode}
```

与えられたノードに対して、指定された直交方向である `axis` ∈ [:X, :Y, :Z] の `SpatialVariable` を定義し、デフォルト値は0に設定されます。
