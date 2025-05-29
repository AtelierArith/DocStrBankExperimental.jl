```
plot2D(nums::T1, param_range1::T2, param_range2::T3; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:AbstractArray,T2<:AbstractVector,T3<:AbstractVector}
```

Plot a 2D phase diagram.

# Arguments

  * `nums::T1`: An array of numbers representing the phase diagram.
  * `param_range1::T2`: A vector representing the range of the first parameter.
  * `param_range2::T3`: A vector representing the range of the second parameter.
  * `labels::Bool=true`: Whether to display axis labels. Default is `true`.
  * `disp::Bool=true`: Whether to display the plot. Default is `true`.
  * `png::Bool=false`: Whether to save the plot as a PNG file. Default is `false`.
  * `pdf::Bool=false`: Whether to save the plot as a PDF file. Default is `false`.
  * `svg::Bool=false`: Whether to save the plot as an SVG file. Default is `false`.
  * `filename::String="phaseDiagram"`: The filename for the saved plot. Default is "phaseDiagram".

# Returns

  * `fig`: The matplotlib figure object.

# Example

```julia
julia>
```
