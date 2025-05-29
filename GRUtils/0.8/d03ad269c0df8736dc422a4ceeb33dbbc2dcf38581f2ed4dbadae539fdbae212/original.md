```
Figure(workstation::Tuple{Float64, Float64}, plots::Vector{PlotObject})
```

Return a new figure, defined by:

  * **`workstation`**: a `Tuple{Float64, Float64}` with the width and height of the   overall plot container (workstation), in pixels.
  * **`plots`**: a vector of [`PlotObject`](@ref) elements, which contain the information of   the individual plots included in the figure.
