```
result = qt_flash(model, q, T, n, method::FlashMethod = GeneralizedXYFlash())
result = qt_flash(model, q, T, n; kwargs...)
```

Routine to solve non-reactive two-phase multicomponent flash problem. with vapour fraction - T specifications. Wrapper around [Clapeyron.xy_flash](@ref), with automatic initial point calculations.  Inputs:

  * `q`, vapour fraction
  * `T`, temperature
  * `z`, vector of number of moles of each species

All keyword arguments are forwarded to [`GeneralizedXYFlash`](@ref).

Outputs:

  * `result`, a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.

!!! note
    Using `qt_flash` with q = 0 or q = 1 is equivalent to calculating bubble or dew pressures. Passing `GeneralizedXYFlash` as a method to [`bubble_pressure`](@ref) of [`dew_pressure`](@ref) will use `qt_flash` to calculate the bubble/dew point.

