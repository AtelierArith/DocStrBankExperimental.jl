```
PrognosticMet <: AbstractSoilDriver
```

A container which holds the soil parameters needed for running biogeochemistry model with the soil model.

  * `ν`: Soil porosity (m³ m⁻³)
  * `θ_a100`: Air-filled porosity at soil water potential of -100 cm H₂O (~ 10 Pa)
  * `b`: Absolute value of the slope of the line relating log(ψ) versus log(S) (unitless)
