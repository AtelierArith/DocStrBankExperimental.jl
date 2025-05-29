```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables{NF},
    initial_conditions::SpeedyWeather.RandomVelocity,
    model::SpeedyWeather.Barotropic
)

```

乱流渦度を初期条件として開始する
