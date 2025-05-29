```
scatter_gplot(X; marker = nothing, ms = 4, plotOrder = :normal, c = :viridis, subplot = 1)
```

SCATTER_GPLOT generates a scatter plot figure, which is for quick viewing of a graph signal. SCATTER_GPLOT!(X; ...) adds a plot to `current` one.

# Input Arguments

  * `X::Matrix{Float64}`: points locations, can be 2-dim or 3-dim.
  * `marker::Array{Float64}`: default is `nothing`. Present different colors given   different signal value at each node.
  * `ms::Array{Float64}`: default is `4`. Present different node sizes given   different signal value at each node.
  * `shape::Symbol`: default is `:none`. Shape of the markers.
  * `mswidth::Number`: default is `0`. Width of the marker stroke border.
  * `msalpha::Number`: default is `nothing`. The opacity for the marker stroke.
  * `plotOrder::Symbol`: default is `:normal`. Optional choices `:s2l` or `:l2s`, i.e.,   plots from the smallest value of `marker` to the largest value or the other way around,   or `:propabs`, ms is automatically set to be proportional to the absolute value   of the marker values.
  * `c::Symbol`: default is `:viridis`. Colors of the markers.
  * `subgplot::Int`: default is `1`. The subplot index.
