```
plot_glacier_heatmaps(
    results::Results,
    variables::Vector{Symbol},
    title_mapping::Dict;
    scale_text_size::Union{Nothing,Float64}=nothing,
    timeIdx::Union{Nothing,Int64}=nothing
) -> Figure
```

Plot heatmaps for glacier variables.

# Arguments

  * `results::Results`: The results object containing the data to be plotted.
  * `variables::Vector{Symbol}`: A list of variables to be plotted.
  * `title_mapping::Dict`: A dictionary mapping variable names to their titles and colormaps.
  * `scale_text_size::Union{Nothing,Float64}`: Optional argument to scale the text size.
  * `timeIdx::Union{Nothing,Int64}`:: Optional argument to select the index at which   data should be plotted when dealing with vector of matrix. Default is nothing   which selects the last element available.

# Returns

  * A plot of the glacier heatmaps.
