```
activity(model::EoSModel,p,T,z=SA[1.0];reference = :pure, phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the activity, defined as:

```julia
log(a) = (μ_mixt - μ_ref) / R̄ / T
```

where `μ_mixt` is the chemical potential of the mixture and `μ_ref` is the reference chemical potential for the model at `p`,`T` conditions, calculated via [`Clapeyron.reference_chemical_potential`](@ref). Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_fugacity_coefficient(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.

If the `μ_ref` keyword argument is not provided, the `reference` keyword is used to specify the reference chemical potential..
