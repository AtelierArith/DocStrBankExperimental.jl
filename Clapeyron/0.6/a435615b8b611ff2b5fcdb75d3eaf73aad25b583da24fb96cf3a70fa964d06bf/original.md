```
joule_thomson_coefficient(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[K/Pa]`

Calculates the joule thomson coefficient, defined as:

```julia
μⱼₜ = -(∂²A/∂V∂T - ∂²A/∂V² * ((T*∂²A/∂T² + V*∂²A/∂V∂T) / (T*∂²A/∂V∂T + V*∂²A/∂V²)))^-1
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_joule_thomson_coefficient(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.

!!! warning "Accurate ideal model required"
    This property requires at least second order ideal model temperature derivatives. If you are computing these properties, consider using a different ideal model than the `BasicIdeal` default (e.g. `EoS(["species"];idealmodel = ReidIdeal)`).

