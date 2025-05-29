```julia
initialize!(
    output::SpeedyWeather.NetCDFOutput{Grid2D, Grid3D, Interpolator},
    feedback::SpeedyWeather.AbstractFeedback,
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
)

```

NetCDF `output`を初期化し、netCDFファイルを作成して`diagn`（および`progn`）の初期条件を保存します。最初のタイムステップの直前に呼び出されるべきです。
