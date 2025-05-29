```
struct PODProjection <: Projection
  basis::AbstractMatrix
end
```

Projection stemming from a truncated proper orthogonal decomposition [`tpod`](@ref)
