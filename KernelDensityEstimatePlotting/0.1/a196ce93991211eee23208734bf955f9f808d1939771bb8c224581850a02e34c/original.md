```julia
getColorsByLength()
getColorsByLength(len)

```

Standardize the length colors used by RoMEPlotting, returns `::Vector{String}`.

Notes:

  * TODO, use `Colors.distinguishable_colors(10, [RGB(1,1,1), RGB(0,0,0)], dropseed=true)`
