```
result = qp_flash(model, q, p, n, method::FlashMethod = GeneralizedXYFlash())
result = qp_flash(model, q, p, n; kwargs...)
```

Routine to solve non-reactive two-phase multicomponent flash problem. with vapour fraction - P specifications. Wrapper around [Clapeyron.xy_flash](@ref), with automatic initial point calculations. Inputs:

  * `q`, vapour fraction
  * `p`, pressure
  * `z`, vector of number of moles of each species

All keyword arguments are forwarded to [`GeneralizedXYFlash`](@ref).

Outputs:

  * `result`, a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.

!!! note
    Using `qp_flash` with q = 0 or q = 1 is equivalent to calculating bubble or dew temperatures. Passing `GeneralizedXYFlash` as a method to [`bubble_temperature`](@ref) of [`dew_temperature`](@ref) will use `qp_flash` to calculate the bubble/dew point.

