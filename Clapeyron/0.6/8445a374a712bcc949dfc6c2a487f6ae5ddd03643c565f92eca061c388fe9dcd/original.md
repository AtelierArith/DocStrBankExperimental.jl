```
azeotrope_pressure(model::EoSModel, T; v0 = x0_azeotrope_pressure(model,T))
```

calculates the azeotrope pressure and properties at a given temperature. Returns a tuple, containing:

  * Azeotrope Pressure `[Pa]`
  * liquid volume at Azeotrope Point [`m³`]
  * vapour volume at Azeotrope Point [`m³`]
  * Azeotrope composition
