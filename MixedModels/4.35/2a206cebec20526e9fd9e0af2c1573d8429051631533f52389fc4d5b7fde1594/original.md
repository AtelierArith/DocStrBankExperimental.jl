```
ranef(m::LinearMixedModel; uscale=false)
```

Return, as a `Vector{Matrix{T}}`, the conditional modes of the random effects in model `m`.

If `uscale` is `true` the random effects are on the spherical (i.e. `u`) scale, otherwise on the original scale.

For a named variant, see [`raneftables`](@ref).
