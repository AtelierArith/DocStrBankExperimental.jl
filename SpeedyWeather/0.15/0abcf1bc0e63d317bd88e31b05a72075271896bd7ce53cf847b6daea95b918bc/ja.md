```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    random_process::SpeedyWeather.NoRandomProcess,
    spectral_transform::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

`NoRandomProcess` は、スペクトルからグリッド空間へのランダムパターンの変換を必要としません。
