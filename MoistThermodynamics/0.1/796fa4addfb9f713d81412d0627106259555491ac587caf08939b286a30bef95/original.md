```
LiquidIcePotTempSHumEquil_given_pressure(θ_liq_ice, p, q_tot)
```

Constructs a [`PhaseEquil`](@ref) thermodynamic state from:

  * `θ_liq_ice` liquid-ice potential temperature
  * `p` pressure
  * `q_tot` total specific humidity
  * `tol` tolerance for saturation adjustment
  * `maxiter` maximum iterations for saturation adjustment
