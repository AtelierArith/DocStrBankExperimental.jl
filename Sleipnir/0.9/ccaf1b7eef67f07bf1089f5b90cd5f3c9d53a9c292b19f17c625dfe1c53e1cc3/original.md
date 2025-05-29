```
plot_glacier_difference_evolution(
    results::Results,
    variables::Vector{Symbol},
    title_mapping;
    tspan::Tuple{F,F}=results.tspan,
    metrics::Vector{String}="difference",
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
) where {F<:AbstractFloat}
```

Plot the evolution of the difference in a glacier variable over time.

# Arguments

  * `results::Results`: The simulation results object containing the data to be plotted.
  * `variables::Vector{Symbol}`: The variable to be plotted.
  * `title_mapping`: A dictionary mapping variable names to their titles.
  * `tspan::Tuple{F,F}`: A tuple representing the start and end time for the simulation.
  * `metrics::Vector{String}`: Metrics to visualize, e.g., `["difference"]`.
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: Size of the figure.

# Returns

  * A plot of the glacier difference evolution.
