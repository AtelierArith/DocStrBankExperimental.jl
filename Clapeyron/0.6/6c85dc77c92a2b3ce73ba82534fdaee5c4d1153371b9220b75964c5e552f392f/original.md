```
mixing(model::EoSModel, p, T, z=SA[1.], property; phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the mixing function for a specified property as:

```julia
f_mix = f(p,T,z) - ∑zᵢ*f_pureᵢ(p,T)
```

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
