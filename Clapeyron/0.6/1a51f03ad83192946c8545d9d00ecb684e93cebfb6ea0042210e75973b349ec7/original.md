```
crit_mix(model::EoSModel,z;v0=x=x0_crit_mix(model,z))
```

Returns the critical mixture point at a ginven composition.

Returns a tuple, containing:

  * Critical Mixture Temperature `[K]`
  * Critical Mixture Pressure `[Pa]`
  * Critical Mixture Volume `[m³]`
