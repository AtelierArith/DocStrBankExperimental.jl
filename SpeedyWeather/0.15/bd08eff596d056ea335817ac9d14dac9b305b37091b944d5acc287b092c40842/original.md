```julia
initialize!(
    implicit::SpeedyWeather.ImplicitPrimitiveEquation,
    dt::Real,
    diagn::SpeedyWeather.DiagnosticVariables{NF},
    geometry::SpeedyWeather.AbstractGeometry,
    geopotential::SpeedyWeather.AbstractGeopotential,
    atmosphere::SpeedyWeather.AbstractAtmosphere,
    adiabatic_conversion::SpeedyWeather.AbstractAdiabaticConversion
)

```

Initialize the implicit terms for the PrimitiveEquation models.
