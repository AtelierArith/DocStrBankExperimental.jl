```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    random_process::SpeedyWeather.AbstractRandomProcess,
    spectral_transform::SpeedyWeather.SpeedyTransforms.SpectralTransform
)

```

`AbstractRandomProcess`のサブタイプである`random processes`の一般的な変換。予測変数のスペクトル`random_pattern`を取得し、`diagn.grid.random_pattern`のスペクトル空間に変換します。
