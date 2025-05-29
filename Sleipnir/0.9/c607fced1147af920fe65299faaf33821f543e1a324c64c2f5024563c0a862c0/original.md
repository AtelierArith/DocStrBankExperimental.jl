```
plot_glacier_statistics_evolution(
    results::Results,
    variables::Vector{Symbol},
    title_mapping;
    metrics="median",
    tspan,
    threshold=0.5,
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
)
```

Plot the evolution of statistics for multiple glacier variables over time.

# Arguments

  * `results::Results`: The simulation results object containing the data to be plotted.
  * `variables::Vector{Symbol}`: A list of variables to be plotted.
  * `title_mapping`: A dictionary mapping variable names to their titles.
  * `metrics`: Metrics to visualize, e.g., "average", "median", "min", "max", and "std". Default is "median".
  * `tspan`: A tuple representing the start and end time for the simulation.
  * `threshold`: A threshold value to filter the data. Default is 0.5.
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: Size of the figure.

# Returns

  * A plot of the glacier statistics evolution.
