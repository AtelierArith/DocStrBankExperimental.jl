```julia
run!(
    simulation::SpeedyWeather.AbstractSimulation;
    period,
    steps,
    output
) -> Union{UnicodePlots.Plot{T, Val{true}} where T<:UnicodePlots.HeatmapCanvas, UnicodePlots.Plot{T, Val{false}} where T<:UnicodePlots.HeatmapCanvas}

```

SpeedyWeather.jlの`simulation`を実行します。`simulation.model`は初期化されていると仮定します。
