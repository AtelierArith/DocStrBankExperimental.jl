```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.Barotropic;
    kwargs...
)

```

予測変数 `progn` のスペクトル状態を診断変数 `diagn` に伝播させ、バロトロピック渦度モデルのために更新します。グリッド渦度、スペクトル流束、およびスペクトルおよびグリッド速度 u, v を更新します。
