```
plt = plotsgaugevelocity(gauge::VisClaw.Gauge; kwargs...)

plt = plotsgaugevelocity(gauges::Vector{VisClaw.Gauge}; kwargs...)

plotsgaugevelocity!(plt::Plots.Plot, gauge::VisClaw.Gauge; kwargs...)

plotsgaugevelocity!(plt::Plots.Plot, gauges::Vector{VisClaw.Gauge}; kwargs...)
```

関数: 計器の波形をプロットする
