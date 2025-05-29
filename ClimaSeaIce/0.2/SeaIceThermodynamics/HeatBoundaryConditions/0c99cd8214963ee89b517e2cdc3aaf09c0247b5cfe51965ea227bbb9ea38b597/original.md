```
FluxFunction(func; parameters=nothing, top_temperature_dependent=false)
```

Return `FluxFunction` representing a flux across an air-ice, air-snow, or ice-water interface. The flux is computed by `func` with the signature

```julia
flux = func(i, j, grid, clock, top_temperature, model_fields)
```

if `isnothing(parameters)`, or

```julia
flux = func(i, j, grid, clock, top_temperature, model_fields, parameters)
```

if `!isnothing(parameters)`. If `func` is `top_temperature_dependent`, then it will be recomputed during a diagnostic solve for the top temperature.
