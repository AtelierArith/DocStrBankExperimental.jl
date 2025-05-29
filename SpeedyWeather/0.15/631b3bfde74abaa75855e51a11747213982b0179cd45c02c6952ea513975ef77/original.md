```julia
initialize!(
    scheme::SpeedyWeather.HeldSuarez,
    model::SpeedyWeather.PrimitiveEquation
)

```

initialize the HeldSuarez temperature relaxation by precomputing terms for the equilibrium temperature Teq.
