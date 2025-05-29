```
setpsplotter(plotter::Symbol=:default)
```

Select a plotting package for use with Pseudospectra.

Currently `:Plots` and `:PyPlot` are implemented. Defaults to `:Plots` unless PyPlot is already imported without Plots.
