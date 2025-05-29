```
kmedoids!(dist::AbstractMatrix, medoids::Vector{Int};
          [kwargs...]) -> KmedoidsResult
```

Update the current cluster `medoids` using the `dist` matrix.

The `medoids` field of the returned `KmedoidsResult` points to the same array as `medoids` argument.

See [`kmedoids`](@ref) for the description of optional `kwargs`.
