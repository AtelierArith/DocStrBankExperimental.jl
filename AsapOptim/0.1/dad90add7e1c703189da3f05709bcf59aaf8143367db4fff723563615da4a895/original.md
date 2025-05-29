```
SpatialVariable(node::T, vector::Vector{Float64}, value::Float64, lowerbound::Float64, upperbound::Float64) where {T<:Asap.AbstractNode}
```

Define a `SpatialVariable` for a given node, in the normalized direction of `vector`, such that:     x' = x*0 + `value` * `vector[1]`       y' = y*0 + `value` * `vector[2]`       z' = z_0 + `value` + `vector[3]`

Where: `lowerbound` ≤ `value` ≤ `upperbound`
