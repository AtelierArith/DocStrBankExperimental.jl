```
fugacity_coefficient(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the fugacity coefficient φᵢ, defined as:

```julia
log(φᵢ) = μresᵢ/RT - log(Z)
```

Where `μresᵢ` is the vector of residual chemical potentials and `Z` is the compressibility factor.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_fugacity_coefficient(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
