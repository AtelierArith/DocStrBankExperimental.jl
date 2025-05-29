```
aqueous_activity(model::EoSModel,p,T,z=SA[1.0]; phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the activity with the reference being infinite dilution in water, defined as:

```julia
log(a) = (μ_mixt - μ_inf) / R̄ / T
```

where `μ_mixt` is the chemical potential of the mixture and `μ_inf` is the chemical potential of the components at infinite dilution in water.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_fugacity_coefficient(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
