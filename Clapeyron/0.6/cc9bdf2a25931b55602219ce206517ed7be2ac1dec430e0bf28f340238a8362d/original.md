```
compressibility_factor(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the compressibility factor `Z`, defined as:

```julia
Z = p*V(p)/R*T
```

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
