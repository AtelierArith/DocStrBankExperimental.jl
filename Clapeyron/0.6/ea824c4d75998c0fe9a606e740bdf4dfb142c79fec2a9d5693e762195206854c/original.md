```
internal_energy_res(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

Default units: `[J]`

Calculates the residual internal energy, defined as:

```julia
U = Ar - T * ∂Ar/∂T
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_internal_energy_res(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
