```julia
activate!(
    simulation::SpeedyWeather.AbstractSimulation,
    tracers::SpeedyWeather.Tracer...
)

```

シミュレーション内で非アクティブ（=凍結された）トレーサーをアクティブにします。これは `simulation.model` の設定のみです。
