```
plot1D(nums::T1, param_range::T2; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:AbstractMatrix,T2<:AbstractVector}
```

Plot a 1D phase diagram.

# Arguments

  * `nums::T1`: A matrix or vector containing the data to be plotted.
  * `param_range::T2`: A vector representing the parameter range.
  * `labels::Bool=true`: Whether to display axis labels. Default is `true`.
  * `disp::Bool=true`: Whether to display the plot. Default is `true`.
  * `png::Bool=false`: Whether to save the plot as a PNG file. Default is `false`.
  * `pdf::Bool=false`: Whether to save the plot as a PDF file. Default is `false`.
  * `svg::Bool=false`: Whether to save the plot as an SVG file. Default is `false`.
  * `filename::String="phaseDiagram"`: The filename for the saved plot. Default is "phaseDiagram".

# Examples

```julia
nums = [1 2 3; 4 5 6]
param_range = [0.1, 0.2, 0.3]
plot1D(nums, param_range)
```

# Returns

  * `fig`: The matplotlib figure object representing the plot.
