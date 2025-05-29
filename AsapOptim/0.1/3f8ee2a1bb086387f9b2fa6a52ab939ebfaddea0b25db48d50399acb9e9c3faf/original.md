```
CoupledVariable(node::Asap.AbstractNode, ref::SpatialVariable, factor::Union{Float64, Vector{Float64}} = 1.0)
```

Make a `SpatialVariable` for `node` that is coupled to `ref.value` along the direction `factor` * `ref.vec`.

`factor` is either a scalar or a vector in R³.
