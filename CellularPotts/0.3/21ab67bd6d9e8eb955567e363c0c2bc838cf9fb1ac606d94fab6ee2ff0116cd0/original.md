```
visualize!(
    plt::AbstractPlot
    cpm::CellPotts;
    colorby=:type,
    cellcolors=nothing,
    migrationcolors=nothing,
    kwargs...)
```

Generates a visualization of the CPM model.

This function will append the given plot with a Cellular Potts Model visualization 
