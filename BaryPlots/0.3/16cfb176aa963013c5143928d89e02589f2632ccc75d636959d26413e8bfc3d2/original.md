```
plot_simplex(; 
    labels::Vector{String} = ["Strategy 1", "Strategy 2", "Strategy 3"], 
    neutral_edges::Vector{Int} = Int[], 
    plot_neutral_dots::Bool = false, 
    p = nothing, 
    kwargs...
) -> Plots.Plot
```

Plots an equilateral triangle representing the simplex for three strategies. Optionally highlights certain edges as "neutral" by adding dotted markers if requested.

# Arguments

  * `labels`: A vector of three strings labeling the corners of the simplex. Default: `["Strategy 1", "Strategy 2", "Strategy 3"]`.
  * `neutral_edges`: A vector of integers indicating which edges are neutral. Edges are indexed as:

      * `1`: Edge between Strategy 1 and Strategy 2
      * `2`: Edge between Strategy 2 and Strategy 3
      * `3`: Edge between Strategy 3 and Strategy 1
  * `plot_neutral_dots`: If `true`, draws a sequence of white dots on each specified neutral edge to visually mark them. Default: `false`.
  * `p`: An existing `Plots.Plot` object to draw on. If `nothing`, a new plot is created.
  * `kwargs`: Additional keyword arguments passed to `plot` for further customization.

# Returns

  * A `Plots.Plot` object displaying the simplex with labeled corners. Edges in `neutral_edges` may be visually highlighted.

# Notes

  * When `plot_neutral_dots` is `false`, the edges in `neutral_edges` are simply not drawn (or drawn in a minimal style, as configured in the source).
  * If you want to add further customizations, you can pass typical Plots.jl arguments (e.g., `linecolor`, `linestyle`, etc.) through `kwargs`.
