```julia
add!(
    output::SpeedyWeather.NetCDFOutput,
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> SpeedyWeather.NetCDFOutput

```

`outputvariables`を`output::NetCDFOutput`の辞書に追加します。すなわち、`output.variables`に追加します。
