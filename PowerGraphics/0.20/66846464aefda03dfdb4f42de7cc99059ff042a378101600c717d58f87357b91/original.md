```
plot_results(results)
```

Makes a plot from a results dictionary object

# Arguments

  * `results::Dict{String, DataFrame`: The results to be plotted

# Accepted Key Words

  * `combine_categories::Bool = false` : plot category values or each value in a category
  * `curtailment::Bool`: plot the curtailment with the variable
  * `set_display::Bool = true`: set to false to prevent the plots from displaying
  * `save::String = "file_path"`: set a file path to save the plots
  * `format::String = "png"`: set a different format for saving a [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) plot. Options include "png", "pdf" and "eps"
  * `seriescolor::Array`: Set different colors for the plots
  * `title::String = "Title"`: Set a title for the plots
  * `stack::Bool = true`: stack plot traces
  * `bar::Bool` : create bar plot
  * `nofill::Bool` : force empty area fill
  * `stair::Bool`: Make a stair plot instead of a stack plot
