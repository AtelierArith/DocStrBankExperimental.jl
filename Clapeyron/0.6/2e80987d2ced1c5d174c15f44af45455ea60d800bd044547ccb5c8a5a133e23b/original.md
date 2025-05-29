```
LLE_pressure(model::EoSModel, T, x; v0 = x0_LLE_pressure(model,T,x))
```

calculates the Liquid-Liquid equilibrium pressure and properties at a given temperature.

Returns a tuple, containing:

  * LLE Pressure `[Pa]`
  * liquid volume of composition `x₁ = x` at LLE Point [`m³`]
  * liquid volume of composition `x₂` at LLE Point  [`m³`]
  * Liquid composition `x₂`
