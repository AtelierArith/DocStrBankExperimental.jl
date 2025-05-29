```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.PrimitiveEquation;
    initialize
)

```

原始方程モデルの診断変数 `diagn` に予測変数 `progn` のスペクトル状態を伝播させます。グリッド渦度、グリッド発散、グリッド温度、圧力（`pres_grid`）および速度 u、v を更新します。
