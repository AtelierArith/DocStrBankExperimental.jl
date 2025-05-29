```
LiquidIcePotTempSHumNonEquil(θ_liq_ice, ρ, q_pt)
```

Constructs a [`PhaseNonEquil`](@ref) thermodynamic state from:

  * `θ_liq_ice` liquid-ice potential temperature
  * `ρ` (moist-)air density
  * `q_pt` phase partition

and, optionally

  * `tol` tolerance for non-linear equation solve
  * `maxiter` maximum iterations for non-linear equation solve
