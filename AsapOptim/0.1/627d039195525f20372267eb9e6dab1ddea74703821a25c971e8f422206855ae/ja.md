```
SpatialVariable(node::T, value::Float64, lowerbound::Float64, upperbound::Float64, axis::Symbol = :Z) where {T<:Asap.AbstractNode}
```

与えられたノードに対して、指定された直交方向である `axis` ∈ [:X, :Y, :Z] の `SpatialVariable` を定義します。
