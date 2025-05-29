```julia
add!(
    model::SpeedyWeather.AbstractModel,
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> Any

```

Add `outputvariables` to the dictionary in `output::NetCDFOutput` of `model`, i.e. at `model.output.variables`.
