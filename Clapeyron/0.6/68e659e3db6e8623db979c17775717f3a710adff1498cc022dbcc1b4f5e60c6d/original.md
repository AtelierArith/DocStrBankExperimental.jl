```
azeotrope_temperature(model::EoSModel, T; v0 = x0_bubble_pressure(model,T,[0.5,0.5]))
```

Calculates the azeotrope temperature and properties at a given pressure. Returns a tuple, containing:

  * Azeotrope Temperature `[K]`
  * liquid volume at Azeotrope Point [`m³`]
  * vapour volume at Azeotrope Point [`m³`]
  * Azeotrope composition
