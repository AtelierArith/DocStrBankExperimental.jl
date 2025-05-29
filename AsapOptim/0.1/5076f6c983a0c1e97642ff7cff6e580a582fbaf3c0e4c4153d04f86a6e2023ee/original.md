```
SpatialVariable(node::T, lowerbound::Float64, upperbound::Float64, axis::Symbol = :Z) where {T<:Asap.AbstractNode}
```

Define a `SpatialVariable` for a given node, in a given Cartesian direction, `axis` ∈ [:X, :Y, :Z] and default value is set to 0.
