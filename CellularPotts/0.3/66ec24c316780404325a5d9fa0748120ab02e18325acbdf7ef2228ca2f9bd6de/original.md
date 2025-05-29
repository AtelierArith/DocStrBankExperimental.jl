```
visualize(
    cpm::CellPotts;
    colorby=:type,
    cellcolors=nothing,
    migrationcolors,
    kwargs...)
```

Generates a visualization of the Cellular Potts Model.

This plotting function builds on Plots.jl, so any possible keywords can be passed on.

The optional `colorby` arguement can be:      1. `:type` to color the cells by cell type     2. `:id` to give each cell a unique color     3. `:none` to not color the cells 

To change the background (Medium) color, supply a color to `background`

A custom set of colors can be supplied, e.g., `colormap = [:red,:blue,:green]`

`migrationcolors` accepts a colormap when a MigrationPenalty is present (cannot be applied to 3D visualizations currently).
