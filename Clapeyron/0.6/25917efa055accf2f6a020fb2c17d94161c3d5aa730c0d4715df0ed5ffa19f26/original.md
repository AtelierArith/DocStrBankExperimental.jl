```
entropy_res(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

Default units: `[J/K]`

Calculates residual entropy, defined as:

```julia
S = -∂Ares/∂T
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_entropy_res(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
