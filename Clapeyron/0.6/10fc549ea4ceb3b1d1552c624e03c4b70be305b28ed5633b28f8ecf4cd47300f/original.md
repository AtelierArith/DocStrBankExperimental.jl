```
psub,vs,vv = sublimation_pressure(model::CompositeModel,T;v0=x0_sublimation_pressure(model,T))
```

Calculates the sublimation pressure of a `CompositeModel` containing a solid and fluid phase EoS, at a specified pressure. You can pass a tuple of initial values for the volumes `(vs0,vv0)`.

returns:

  * Sublimation Pressure [`Pa`]
  * Sublimation solid volume at specified temperature [`m³`]
  * Sublimation vapour volume at specified temperature [`m³`]
