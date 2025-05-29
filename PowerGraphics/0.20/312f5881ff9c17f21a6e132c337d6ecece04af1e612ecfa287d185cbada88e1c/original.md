```
plot_dataframe!(plot, df)
plot_dataframe!(plot, df, time_range)
```

Plots data from a [`DataFrames.DataFrame`](@extref) where each row represents a time period and each column represents a trace

# Arguments

  * `plot`: existing plot handle, such as the result of [`plot()`](@extref RecipesBase.plot)
  * `df::DataFrames.DataFrame`: `DataFrame` where each row represents a time period and each column represents a trace.

If only the `DataFrame` is provided, it must have a column of `DateTime` values.

  * `time_range::Union{DataFrames.DataFrame, Array, StepRange}`: The time periods of the data

# Accepted Key Words

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
