```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables{NF},
    initial_conditions::SpeedyWeather.JablonowskiTemperature,
    model::SpeedyWeather.PrimitiveEquation
)

```

JablonowskiとWilliamsonによる初期条件、2006年、QJR Meteorol. Soc
