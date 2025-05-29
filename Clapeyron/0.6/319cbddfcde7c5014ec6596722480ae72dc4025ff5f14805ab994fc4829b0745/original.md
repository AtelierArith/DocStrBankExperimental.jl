```
UCST_pressure(model::EoSModel,T;v0=x0_UCST_pressure(model,T))
UCST_mix(model::EoSModel,T;v0=x0_UCST_pressure(model,T))
```

Calculates the Upper critical solution point of a mixture at a given Temperature.

returns:

  * UCST Pressure [`Pa`]
  * volume at UCST Point [`m³`]
  * molar composition at UCST Point
