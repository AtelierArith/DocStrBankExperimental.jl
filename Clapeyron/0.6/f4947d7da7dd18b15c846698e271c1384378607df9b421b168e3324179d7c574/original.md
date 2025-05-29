```
pm,vs,vl = melting_pressure(model::CompositeModel,T;v0=x0_melting_pressure(model,T))
```

Calculates the melting pressure of a `CompositeModel` containing a solid and fluid phase EoS, at a specified pressure. You can pass a tuple of initial values for the volumes `(vs0,vl0)`.

returns:

  * Melting Pressure [`Pa`]
  * melting solid volume at specified temperature [`m³`]
  * melting liquid volume at specified temperature [`m³`]
