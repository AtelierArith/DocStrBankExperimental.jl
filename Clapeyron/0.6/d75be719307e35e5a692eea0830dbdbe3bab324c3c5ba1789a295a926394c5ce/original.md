```
fundamental_derivative_of_gas_dynamics(model::EoSModel, p, T, z=SA[1.]; phase=:gas, threaded=true, vol0=nothing)::Symbol
```

Calculates the fundamental derivative of gas dynamics.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_enthalpy(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
