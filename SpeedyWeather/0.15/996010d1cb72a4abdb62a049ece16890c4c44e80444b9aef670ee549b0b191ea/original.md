```julia
initialize!(
    orog::SpeedyWeather.EarthOrography,
    P::SpeedyWeather.AbstractPlanet,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

Initialize the arrays `orography`, `geopot_surf` in `orog` by reading the orography field from file.
