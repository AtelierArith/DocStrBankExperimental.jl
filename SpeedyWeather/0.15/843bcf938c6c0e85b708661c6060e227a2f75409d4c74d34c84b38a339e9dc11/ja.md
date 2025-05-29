```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables{NF},
    initial_conditions::SpeedyWeather.RandomWaves,
    model::SpeedyWeather.ShallowWater
)

```

浅水方程における界面変位ηのためのランダム初期条件。流れ(u, v)は初めはゼロです。これにより、地形と相互作用する重力波が発生します。
