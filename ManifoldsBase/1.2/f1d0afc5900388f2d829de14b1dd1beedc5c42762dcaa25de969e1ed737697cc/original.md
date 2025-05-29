```
set_component!(M::AbstractPowerManifold, q, p, idx...)
```

Set the component of a point `q` on an [`AbstractPowerManifold`](@ref) `M` at index `idx` to `p`, which itself is a point on the [`AbstractManifold`](@ref) the power manifold is build on.
