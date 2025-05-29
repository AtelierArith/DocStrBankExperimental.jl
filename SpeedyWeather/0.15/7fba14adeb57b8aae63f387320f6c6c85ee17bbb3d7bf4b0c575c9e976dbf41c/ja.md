```julia
isscheduled(
    S::SpeedyWeather.Schedule,
    clock::SpeedyWeather.Clock
) -> Bool

```

clockで与えられたタイムステップで（例えばコールバック）がスケジュールされるべきかどうかを評価します。このタイムステップでの実行がスケジュールされている場合はtrueを、実行がない場合はfalseを返します。
