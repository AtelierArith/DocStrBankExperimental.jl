```
molar_density(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[mol/m^3]`

Calculates the molar density, defined as:

```julia
ρₙ = ∑nᵢ/V
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_molar_density(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
