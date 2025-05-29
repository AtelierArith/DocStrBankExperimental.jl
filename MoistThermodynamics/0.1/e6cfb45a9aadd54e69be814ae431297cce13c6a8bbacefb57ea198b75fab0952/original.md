```
LiquidIcePotTempSHumEquil(θ_liq_ice, ρ, q_tot)
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from:

  * `θ_liq_ice` liquid-ice potential temperature
  * `ρ` (moist-)air density
  * `q_tot` total specific humidity
  * `tol` tolerance for saturation adjustment
  * `maxiter` maximum iterations for saturation adjustment
