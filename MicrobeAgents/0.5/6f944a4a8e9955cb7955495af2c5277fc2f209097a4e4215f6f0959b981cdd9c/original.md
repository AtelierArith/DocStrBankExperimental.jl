```
AbstractChemoattractant{D,T}
```

Abstract type for chemoattractants. Requires dimensionality (`D`) and number type (`T`, typically `Float64`).

The interface is defined by four core functions that operate on `AgentBasedModel`s:

  * `chemoattractant`: returns the chemoattractant object
  * `concentration`: returns the function for the concentration field
  * `gradient`: returns the function for the concentration gradient
  * `time_derivative`: returns the function for the concentration ramp
  * `chemoattractant_diffusivity`: returns the thermal diffusivity of the chemoattractant
