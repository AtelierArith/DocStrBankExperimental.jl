```julia
initialize!(
    orog::SpeedyWeather.EarthOrography,
    P::SpeedyWeather.AbstractPlanet,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

`orog`内の配列`orography`、`geopot_surf`をファイルからの地形場を読み込むことで初期化します。
