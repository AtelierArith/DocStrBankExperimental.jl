```
plt = plotsgaugevelocity(gauge::VisClaw.Gauge; kwargs...)

plt = plotsgaugevelocity(gauges::Vector{VisClaw.Gauge}; kwargs...)

plotsgaugevelocity!(plt::Plots.Plot, gauge::VisClaw.Gauge; kwargs...)

plotsgaugevelocity!(plt::Plots.Plot, gauges::Vector{VisClaw.Gauge}; kwargs...)
```

Function: plot waveforms of gauges
