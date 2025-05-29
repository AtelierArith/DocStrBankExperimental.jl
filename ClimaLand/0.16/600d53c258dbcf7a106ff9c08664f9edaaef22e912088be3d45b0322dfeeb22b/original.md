```
PrescribedPrecipitation{FT, LP} <: AbstractAtmosphericDrivers{FT}
```

Container for holding prescribed precipitation driver for models which only require precipitation (RichardsModel).

  * `liquid_precip`: Precipitation (m/s) function of time: positive by definition
