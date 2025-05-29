```
isentropic_compressibility(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[Pa^-1]`

Calculates the isentropic compressibility, defined as:

```julia
κS = (V*( ∂²A/∂V² - ∂²A/∂V∂T^2 / ∂²A/∂T² ))^-1
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_isentropic_compressibility(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.

!!! warning "Accurate ideal model required"
    This property requires at least second order ideal model temperature derivatives. If you are computing these properties, consider using a different ideal model than the `BasicIdeal` default (e.g. `EoS(["species"];idealmodel = ReidIdeal)`).

