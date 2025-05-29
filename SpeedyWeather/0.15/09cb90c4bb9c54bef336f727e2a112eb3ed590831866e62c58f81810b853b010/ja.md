```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.ShallowWater;
    kwargs...
)

```

予測変数 `progn` のスペクトル状態を診断変数 `diagn` に伝播させ、浅水モデルのために更新します。グリッド渦度、グリッド発散、グリッドインターフェース変位（`pres_grid`）および速度 u、v を更新します。
