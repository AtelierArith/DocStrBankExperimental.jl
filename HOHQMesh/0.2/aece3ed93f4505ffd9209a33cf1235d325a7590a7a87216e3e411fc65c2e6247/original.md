```
plotProject!(proj::Project, plotOptions::Int = 0)
```

Plot objects specified by the `plotOptions`. Construct the `plotOptions` by the sum of what is to be drawn from the choices `MODEL`, `GRID`, `MESH`, `REFINEMENTS`.

Example: To plot the model and the grid, `plotOptions = MODEL + GRID`. To plot just the mesh, `plotOptions = MESH`.

To plot everything, `plotOptions = MODEL + GRID + MESH + REFINEMENTS`

Contents are overlaid in the order: `GRID`, `MESH`, `MODEL`, `REFINEMENTS`

!!! note "Requires Makie.jl"
    Please note that for this function to work, you need to load Makie.jl in your REPL (e.g., by calling `using GLMakie`).

