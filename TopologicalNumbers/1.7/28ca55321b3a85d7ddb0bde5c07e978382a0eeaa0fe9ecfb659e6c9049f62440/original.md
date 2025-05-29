```
plot2D(result::NamedTuple; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram")
```

Plot a 2D phase diagram.

# Arguments

  * `result::NamedTuple`: A named tuple containing the result data.
  * `labels::Bool=true`: Whether to display axis labels.
  * `disp::Bool=true`: Whether to display the plot.
  * `png::Bool=false`: Whether to save the plot as a PNG file.
  * `pdf::Bool=false`: Whether to save the plot as a PDF file.
  * `svg::Bool=false`: Whether to save the plot as an SVG file.
  * `filename::String="phaseDiagram"`: The filename for the saved plot.

# Returns

  * `fig`: The matplotlib figure object.

# Example

```julia
julia>
```
