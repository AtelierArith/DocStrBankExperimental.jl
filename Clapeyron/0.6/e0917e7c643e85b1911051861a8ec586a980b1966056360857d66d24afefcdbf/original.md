```
LLE_temperature(model::EoSModel, p, x; T0 = x0_LLE_temperature(model,p,x))
```

calculates the Liquid-Liquid equilibrium temperature and properties at a given pressure.

Returns a tuple, containing:

  * LLE Pressure `[Pa]`
  * liquid volume of composition `x₁ = x` at LLE Point [`m³`]
  * liquid volume of composition `x₂` at LLE Point  [`m³`]
  * Liquid composition `x₂`
