```
adiabatic_index(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

Default units: `[J/K]`

Calculates the isobaric heat capacity, defined as:

```julia
γ = Cp/Cv
```

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_adiabatic_index(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.

!!! warning "Accurate ideal model required"
    This property requires at least second order ideal model temperature derivatives. If you are computing these properties, consider using a different ideal model than the `BasicIdeal` default (e.g. `EoS(["species"];idealmodel = ReidIdeal)`).

