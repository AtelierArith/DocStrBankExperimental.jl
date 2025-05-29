```
updatePlot!(proj::Project, plotOptions::Int)
```

Replot with the new plotOptions = combinations (sums) of

```
GRID, MESH, MODEL, REFINEMENTS
```

Example: `updatePlot!(p, MESH + MODEL)`

!!! note "Requires Makie.jl"
    Please note that for this function to work, you need to load Makie.jl in your REPL (e.g., by calling `using GLMakie`).

