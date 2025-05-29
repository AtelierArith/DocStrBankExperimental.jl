```
plot_glacier_integrated_volume(
    results,
    variables,
    title_mapping;
    tspan,
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
)
```

Plot the integrated volume of a glacier variable over time.

# Arguments

  * `results::Results`: The results object containing the data to be plotted.
  * `variables::Vector{Symbol}`: The variable to be plotted.
  * `title_mapping`: A dictionary mapping variable names to their titles.
  * `tspan`: A tuple representing the start and end time for the simulation.
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: Size of the figure.

# Returns

  * A plot of the glacier integrated volume.
