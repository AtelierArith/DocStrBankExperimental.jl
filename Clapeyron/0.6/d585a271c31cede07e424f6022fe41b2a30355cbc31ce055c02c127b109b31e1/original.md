```
isobaric_expansivity(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[K^-1]`

Calculates the isobaric expansivity, defined as:

```julia
α = -∂²A/∂V∂T / (V*∂²A/∂V²)
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_isobaric_expansivity(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
