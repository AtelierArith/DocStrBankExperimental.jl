```
getcluster(y::Vector{<:Real}, u₁::Real, u₂::Real)
```

Extract the clusters from vector `y`.

A cluster is defined as a sequence of values higher than threshold u₂ with at least a value higher than threshold u₁.

See also [`Cluster`](@ref).
