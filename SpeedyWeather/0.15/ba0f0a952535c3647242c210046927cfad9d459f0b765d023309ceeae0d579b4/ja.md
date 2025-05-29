```julia
add!(
    model::SpeedyWeather.AbstractModel,
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> Any

```

`outputvariables`を`model`の`output::NetCDFOutput`の辞書に追加します。すなわち、`model.output.variables`に追加します。
