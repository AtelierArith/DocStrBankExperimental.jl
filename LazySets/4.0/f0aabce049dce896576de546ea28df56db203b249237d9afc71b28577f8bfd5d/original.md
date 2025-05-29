# Extended help

```
linear_map(M::AbstractMatrix, P::LazySet; kwargs...)
```

### Algorithm

The default implementation assumes that `P` is polyhedral and applies an algorithm based on the set type (see [`_linear_map_polyhedron`](@ref)).
