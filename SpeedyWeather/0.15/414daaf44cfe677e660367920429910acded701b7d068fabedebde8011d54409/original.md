```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractOutputVariable},
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> Dict{Symbol, SpeedyWeather.AbstractOutputVariable}

```

Add `outputvariables` to a dictionary defining the variables subject to NetCDF output.
