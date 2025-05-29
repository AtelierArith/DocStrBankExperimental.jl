```julia
deactivate!(
    simulation::SpeedyWeather.AbstractSimulation,
    tracers::SpeedyWeather.Tracer...
)

```

シミュレーション内のトレーサーを無効にします。これは `simulation.model` の設定のみです。
