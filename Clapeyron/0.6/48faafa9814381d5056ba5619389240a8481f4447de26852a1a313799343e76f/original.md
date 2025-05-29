```
result = ts_flash(model, T, s, n, method::FlashMethod = GeneralizedXYFlash())
result = ts_flash(model, T, s, n; kwargs...)
```

Routine to solve non-reactive two-phase multicomponent flash problem. with T-S specifications. Wrapper around [Clapeyron.xy_flash](@ref), with automatic initial point calculations.  Inputs:

  * `T`, temperature
  * `s`, entropy
  * `z`, vector of number of moles of each species

All keyword arguments are forwarded to [`GeneralizedXYFlash`](@ref).

Outputs:

  * `result`, a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.
