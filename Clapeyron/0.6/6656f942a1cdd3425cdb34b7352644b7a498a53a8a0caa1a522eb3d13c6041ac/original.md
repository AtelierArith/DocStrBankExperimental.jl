```
identify_phase(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)::Symbol
```

Returns the phase of a fluid at the conditions specified by `V`, `T` and `z`. Uses the phase identification parameter criteria from `Clapeyron.pip`

returns `:liquid` if the phase is liquid (or liquid-like), `:vapour` if the phase is vapour (or vapour-like), and `:unknown` if the calculation of the phase identification parameter failed.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_enthalpy(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
