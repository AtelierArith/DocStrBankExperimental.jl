```
hexbin(xs, ys; kwargs...)
```

Plots a heatmap with hexagonal bins for the observations `xs` and `ys`.

## Attributes

### Specific to `Hexbin`

  * `weights = nothing`: Weights for each observation.  Can be `nothing` (each observation carries weight 1) or any `AbstractVector{<: Real}` or `StatsBase.AbstractWeights`.
  * `bins = 20`: If an `Int`, sets the number of bins in x and y direction. If a `Tuple{Int, Int}`, sets the number of bins for x and y separately.
  * `cellsize = nothing`: If a `Real`, makes equally-sided hexagons with width `cellsize`. If a `Tuple{Real, Real}` specifies hexagon width and height separately.
  * `threshold::Int = 1`: The minimal number of observations in the bin to be shown. If 0, all zero-count hexagons fitting into the data limits will be shown.
  * `colorscale = identity`: A function to scale the number of observations in a bin, eg. log10.

### Generic

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`
  * `colorrange::Tuple(<:Real,<:Real} = Makie.automatic`  sets the values representing the start and end points of `colormap`.
