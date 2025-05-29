```
UCST_temperature(model::EoSModel,p,x;v0 = nothing)
```

Calculates the Upper critical solution point of a mixture at a given pressure.

inputs:

  * model: EoS model
  * p: pressure [`Pa`]
  * v0 (optional): an initial guess,consisting of a tuple of initial temperature, volume and composition.

returns:

  * UCST Temperature [`K`]
  * volume at UCST Point [`m³`]
  * molar composition at UCST Point
