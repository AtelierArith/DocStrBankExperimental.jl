```
plt = plotscoastline(topo::VisClaw.Topo; kwargs...)
plt = plotscoastline(topo::VisClaw.Topo, wetdry::VisClaw.Topo; kwargs...)

plotscoastline!(plt::Plots.Plot, topo::VisClaw.Topo; kwargs...)
plotscoastline!(plt::Plots.Plot, topo::VisClaw.Topo, wetdry::VisClaw.Topo; kwargs...)
```

plot coastlines from topography and bathymetry data using Plots
