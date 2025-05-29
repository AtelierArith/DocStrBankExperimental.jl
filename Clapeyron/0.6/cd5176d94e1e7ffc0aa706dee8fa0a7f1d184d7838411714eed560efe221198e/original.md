```
result = vt_flash(model, v, T, n, method::FlashMethod = GeneralizedXYFlash())
result = vt_flash(model, v, T, n; kwargs...)
```

Routine to solve non-reactive two-phase multicomponent flash problem. with V-T specifications. Wrapper around [Clapeyron.xy_flash](@ref), with automatic initial point calculations.  Inputs:

  * `v`, volume
  * `T`, temperature
  * `z`, vector of number of moles of each species

All keyword arguments are forwarded to [`GeneralizedXYFlash`](@ref).

Outputs:

  * `result`, a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.
