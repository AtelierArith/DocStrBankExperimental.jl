```
plot1D(::T1, nums::T2, param_range::T3; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:SecondChernAlgorithms,T2<:AbstractVector,T3<:AbstractVector}
```

Plot a 1D phase diagram.

# Arguments

  * `::T1`: An object of type `T1` that implements the `SecondChernAlgorithms` interface.
  * `nums::T2`: A vector of numbers representing the values to be plotted.
  * `param_range::T3`: A vector representing the parameter range.
  * `labels::Bool=true`: Whether to display labels on the plot. Default is `true`.
  * `disp::Bool=true`: Whether to display the plot. Default is `true`.
  * `png::Bool=false`: Whether to save the plot as a PNG file. Default is `false`.
  * `pdf::Bool=false`: Whether to save the plot as a PDF file. Default is `false`.
  * `svg::Bool=false`: Whether to save the plot as an SVG file. Default is `false`.
  * `filename::String="phaseDiagram"`: The filename for the saved plot. Default is `"phaseDiagram"`.

# Examples

```julia
plot1D(obj, nums, param_range)
```

# Returns

  * `fig`: The matplotlib figure object representing the plot.
