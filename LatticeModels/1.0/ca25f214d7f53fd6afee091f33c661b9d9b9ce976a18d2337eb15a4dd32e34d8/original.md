```
PointFluxes{GaugeT} <: AbstractField
```

An object representing a collection of small magnetic fluxes through given points. The field is directed along z-axis.

## Fields

  * `fluxes`: The magnetic flux values.
  * `points`: A vector of `NTuple{2,Float64}` points.
