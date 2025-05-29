```
isothermal_compressibility(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[Pa^-1]`

Calculates the isothermal compressibility, defined as:

```julia
κT = -(V*∂p/∂V)^-1
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_isothermal_compressibility(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
