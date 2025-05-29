```
GasExchangeBoundaryCondition(; water_concentration,
                               air_concentration,
                               transfer_velocity,
                               wind_speed)
```

Returns a `FluxBoundaryCondition` for the gas exchange between `water_concentration` and `air_concentration` with `transfer_velocity`.

`water_concentration`, `air_concentration` and `wind_speed` can either be numbers,  functions of the form `(x, y, t)`, functions of the form `(i, j, grid, clock, model_fields)`  if `discrete_form` is set to true, or any kind of `Field`.

`water_concentration` should usually be a `[Tracer]Concentration` where is the name of the tracer (you will have to build your own if this is not `OxygenConcentration`),  or a `CarbonDioxideConcentration` which diagnoses the partial pressure of CO₂ in the water.

`transfer_velocity` should be a function of the form `k(u₁₀, T)`.
