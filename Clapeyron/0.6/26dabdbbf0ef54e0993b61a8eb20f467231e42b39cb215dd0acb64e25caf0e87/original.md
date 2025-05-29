```
result = ph_flash(model, p, h, n, method::FlashMethod = GeneralizedXYFlash())
result = ph_flash(model, p, h, n; kwargs...)
```

Routine to solve non-reactive two-phase multicomponent flash problem. with P-H specifications. Wrapper around [Clapeyron.xy_flash](@ref), with automatic initial point calculations.  Inputs:

  * `p`, pressure
  * `h`, enthalpy
  * `z`, vector of number of moles of each species

All keyword arguments are forwarded to [`GeneralizedXYFlash`](@ref).

Outputs:

  * `result`, a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.
