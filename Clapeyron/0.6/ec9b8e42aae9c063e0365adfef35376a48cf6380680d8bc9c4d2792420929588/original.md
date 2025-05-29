```
VLLE_temperature(model::EoSModel, p; T0 = x0_LLE_temperature(model,p))
```

calculates the Vapor-Liquid-Liquid equilibrium temperature and properties of a binary mixture at a given temperature.

Returns a tuple, containing:

  * VLLE temperature `[K]`
  * Liquid volume of composition `x₁` at VLLE Point [`m³`]
  * Liquid volume of composition `x₂` at VLLE Point  [`m³`]
  * Vapour volume of composition `y` at VLLE Point  [`m³`]
  * Liquid composition `x₁`
  * Liquid composition `x₂`
  * Liquid composition `y`
