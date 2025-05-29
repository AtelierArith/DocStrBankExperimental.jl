```
CoupledVariable(node::T, ref::SpatialVariable, vec::Vector{Float64}) where {T<:Asa.AbstractNode}
```

Make a `SpatialVariable` for `node` that is coupled to `ref.value` but with along a different vector `vector`
