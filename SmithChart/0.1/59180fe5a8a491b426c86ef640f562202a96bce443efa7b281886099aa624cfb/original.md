```
datamarkers(ax::SmithAxis, gp::GridPosition, priority = 100; fontsize = 10.0, title = true, kwargs...)
```

Allows creating data markers with DOUBLE CLICK on the lines or scatter plots.

  * ax::SmithAxis is the `SmithAxis`.
  * gp::GridPosition is a GridPosition. Example: fig[1,2]
  * markerdict::Dict{Int, ComplexF64} is a Dict that stores the data of each marker. If you don't need

the values you can ignore this argument.
