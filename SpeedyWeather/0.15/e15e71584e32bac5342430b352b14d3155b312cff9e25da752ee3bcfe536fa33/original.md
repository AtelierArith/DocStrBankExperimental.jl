```julia
run!(
    simulation::SpeedyWeather.AbstractSimulation;
    period,
    steps,
    output
) -> Union{UnicodePlots.Plot{T, Val{true}} where T<:UnicodePlots.HeatmapCanvas, UnicodePlots.Plot{T, Val{false}} where T<:UnicodePlots.HeatmapCanvas}

```

Run a SpeedyWeather.jl `simulation`. The `simulation.model` is assumed to be initialized.
