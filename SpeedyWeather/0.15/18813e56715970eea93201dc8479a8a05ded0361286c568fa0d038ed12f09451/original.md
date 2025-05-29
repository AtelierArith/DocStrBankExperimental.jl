```julia
initialize!(
    scheme::SpeedyWeather.JablonowskiRelaxation,
    model::SpeedyWeather.PrimitiveEquation
)

```

initialize the JablonowskiRelaxation temperature relaxation by precomputing terms for the equilibrium temperature Teq and the frequency (strength of relaxation).
