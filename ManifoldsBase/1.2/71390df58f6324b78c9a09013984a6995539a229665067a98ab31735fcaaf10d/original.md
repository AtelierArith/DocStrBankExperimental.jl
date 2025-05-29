```
fill!(P, p, M::AbstractPowerManifold)
```

Fill a point `P` on the [`AbstractPowerManifold`](@ref) `M`, setting every entry to `p`.

!!! note
    while usually the manifold is the first argument in all functions in `ManifoldsBase.jl`, we follow the signature of `fill!`, where the power manifold serves are the size information.

