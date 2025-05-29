```julia
initialize!(
    orog::SpeedyWeather.ZonalRidge,
    P::SpeedyWeather.AbstractPlanet,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform,
    G::SpeedyWeather.Geometry
)

```

Initialize the arrays `orography`, `geopot_surf` in `orog` following  Jablonowski and Williamson, 2006.
