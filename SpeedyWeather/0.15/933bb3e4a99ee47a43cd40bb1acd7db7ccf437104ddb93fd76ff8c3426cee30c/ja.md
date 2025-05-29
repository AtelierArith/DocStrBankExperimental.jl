```julia
initialize!(
    callback::SpeedyWeather.GlobalSurfaceTemperatureCallback{NF},
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
) -> Int64

```

コールバックの `callback.temp` ベクトルを初期化し、すべてのタイムステップでの全球平均表面温度を記録します。正しい長さのベクトル（要素数 = 総タイムステップ数 + 1）を割り当て、初期条件の全球表面温度を格納します。
