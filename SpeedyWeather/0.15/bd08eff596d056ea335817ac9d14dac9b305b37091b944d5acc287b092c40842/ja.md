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

原始方程モデルの暗黙的項を初期化します。
