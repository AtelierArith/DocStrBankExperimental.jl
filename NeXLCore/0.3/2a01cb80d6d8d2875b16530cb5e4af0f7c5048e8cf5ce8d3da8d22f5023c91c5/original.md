```
nonneg(mat::Material{U,V}, elm::Element)::U where {U<:AbstractFloat,V<:AbstractFloat}
nonneg(mat::Material{UncertainValue,V}, elm::Element)::Float64 where {V<:AbstractFloat}
nonneg(mat::Material)::Material
```

Returns the mass fraction of `elm::Element` truncated to be non-negative.  Negative values are returned as 0.0. Positive values are returned as is.
