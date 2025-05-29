```
fill(p, M::AbstractPowerManifold)
```

Create a point on the [`AbstractPowerManifold`](@ref) `M`, where every entry is set to the point `p`.

!!! note
    while usually the manifold is a first argument in all functions in `ManifoldsBase.jl`, we follow the signature of `fill`, where the power manifold serves are the size information.

