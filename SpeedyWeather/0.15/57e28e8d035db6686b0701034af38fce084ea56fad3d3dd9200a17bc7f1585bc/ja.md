```julia
initialize!(
    orog::SpeedyWeather.ZonalRidge,
    P::SpeedyWeather.AbstractPlanet,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform,
    G::SpeedyWeather.Geometry
)

```

`orog`内の配列`orography`、`geopot_surf`をJablonowskiとWilliamson, 2006に従って初期化します。
