```
plt = plotscoastline(topo::VisClaw.Topo; kwargs...)
plt = plotscoastline(topo::VisClaw.Topo, wetdry::VisClaw.Topo; kwargs...)

plotscoastline!(plt::Plots.Plot, topo::VisClaw.Topo; kwargs...)
plotscoastline!(plt::Plots.Plot, topo::VisClaw.Topo, wetdry::VisClaw.Topo; kwargs...)
```

地形および水深データを使用して海岸線をプロットするには、Plotsを使用します。
