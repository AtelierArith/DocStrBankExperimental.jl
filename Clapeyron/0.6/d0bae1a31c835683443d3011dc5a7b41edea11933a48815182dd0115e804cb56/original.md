```
reference_chemical_potential(model::EoSModel,p,T,reference; phase=:unknown, threaded=true, vol0=nothing)
```

Returns a reference chemical potential. used in calculation of `activity` and actitivy_coefficient. there are two available references:

  * `:pure`: the reference potential is a pure component at specified `T`, `p` and `phase`
  * `:aqueous`: the chemical potential of the pure components at specified `T`, `p` and `phase`
  * `:sat_pure_T`:  the reference potential is the pure saturated liquid phase at specified `T`.
  * `:zero`: the reference potential is equal to zero for all components (used for `ActivityModel`)

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
