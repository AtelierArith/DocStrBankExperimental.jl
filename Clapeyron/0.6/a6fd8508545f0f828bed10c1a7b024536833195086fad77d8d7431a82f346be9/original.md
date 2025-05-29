```
pm,vs,vl = sublimation_temperature(model::CompositeModel,T;v0=x0_sublimation_pressure(model,T))
```

Calculates the sublimation temperature of a `CompositeModel` containing a solid and fluid phase EoS, at a specified pressure. You can pass a tuple of initial values for the volumes `(vs0,vl0)`.

returns:

  * Sublimation Temperature [`K`]
  * sublimation solid volume at specified pressure [`m³`]
  * sublimation vapour volume at specified pressure [`m³`]
