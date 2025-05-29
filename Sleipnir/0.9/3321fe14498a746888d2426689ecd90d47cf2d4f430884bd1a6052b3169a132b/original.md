```
plot_glacier(results::Results, plot_type::String, variables::Vector{Symbol}; kwargs...) -> Figure
```

Generate various types of plots for glacier data.

# Arguments

  * `results::Results`: The results object containing the data to be plotted.
  * `plot_type::String`: Type of plot to generate. Options are:

      * "heatmaps": Heatmaps for glacier variables like `:H`, `:H₀`, `:S`, `:B`, `:V`, `:Vx`, `:Vy`, `:V_ref`.
      * "evolution difference": Temporal difference metrics (between start and end) for a variable, with optional metrics like "hist" (histogram) and "difference".
      * "evolution statistics": Temporal statistical metrics for a variable, with optional metrics like "average", "median", "min", "max", and "std".
      * "integrated volume": Temporal evolution of the integrated ice volume for a variable.
      * "bias": Scatter plot to visualize the bias between two variables.
  * `variables::Vector{Symbol}`: Variables to be plotted, e.g., `:H`.

# Optional Keyword Arguments

  * `tspan`: A tuple representing the start and end time for the simulation.
  * `metrics`: Metrics to visualize, e.g., `["average"]` for statistics, `["difference"]` for difference.
  * `scale_text_size::Union{Nothing,Float64}`: Optional argument to scale the text size for heatmaps.
  * `threshold::Vector{F}`: Threshold values for filtering data in bias plots.
  * `figsize::Tuple{Int64, Int64}`: Size of the figure.

# Returns

  * A `Figure` object containing the desired visualization.

# Notes

  * Ensure the `variables` and `kwargs` match the requirements of the specified `plot_type`.
  * The function routes requests to specific plotting functions based on `plot_type`.
