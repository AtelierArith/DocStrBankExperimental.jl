```julia
add!(
    output::SpeedyWeather.NetCDFOutput,
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> SpeedyWeather.NetCDFOutput

```

Add `outputvariables` to the dictionary in `output::NetCDFOutput`, i.e. at `output.variables`.
