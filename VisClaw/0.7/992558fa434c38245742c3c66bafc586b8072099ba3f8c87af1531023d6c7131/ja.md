```
plt = plotsgaugewaveform(gauge::VisClaw.Gauge; kwargs...)

plt = plotsgaugewaveform(gauges::Vector{VisClaw.Gauge}; kwargs...)

plotsgaugewaveform!(plt::Plots.Plot, gauge::VisClaw.Gauge; kwargs...)

plotsgaugewaveform!(plt::Plots.Plot, gauges::Vector{VisClaw.Gauge}; kwargs...)
```

関数: ゲージの波形をプロットする
