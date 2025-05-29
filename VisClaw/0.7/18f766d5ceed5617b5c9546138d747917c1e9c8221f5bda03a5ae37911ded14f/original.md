```
plt = plotsgaugelocation(gauge::VisClaw.Gauge; offset=(0,0), font::Plots.Font, annotation_str=@sprintf(" %s",gauge.id), kwargs...)

plt = plotsgaugelocation(gauges::Vector{VisClaw.Gauge}; offset=(0,0), font::Plots.Font, annotation_str=" ", kwargs...)

plotsgaugelocation!(plt::Plots.Plot, gauge::VisClaw.Gauge; offset=(0,0), font::Plots.Font, annotation_str=@sprintf(" %s",gauge.id), kwargs...)

plotsgaugelocation!(plt, gauges::Vector{VisClaw.Gauge}; offset=(0,0), font::Plots.Font, annotation_str=" ", kwargs...)
```

Function: plot a gauge location (with scatter plot) using Plots
