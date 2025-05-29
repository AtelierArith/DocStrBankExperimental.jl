```
plotx(X, Y...; xlabel="time [s]", ylabels=nothing, labels=nothing, xlims=nothing, ylims=nothing, ann=nothing, 
           scatter=false, title="", fig="", title="", ysize=14, yzoom=1.0, disp=false)
```

Create an oscilloscope like plot with multiple y axes and one x axis.

# Arguments

  * `X::Vector`: x-axis data
  * `Y::Vector`: any number of comma seperated y-axis vectors
  * `xlabel::String`: x-axis label
  * `ylabels::Vector{String}`: y-axis labels
  * `labels::Vector{String}`: labels for each y-axis
  * `xlims::Tuple{Float64, Float64}`: x-axis limits
  * `ylims::Tuple{Float64, Float64}`: y-axis limits
  * `ann::Vector{Tuple{Float64, Float64, String}}`: annotations
  * `scatter::Bool`: scatter plot
  * `fig::String`: figure name
  * `title::String`: title
  * `ysize::Int`: y-axis label size
  * `yzoom::Float64`: y-axis zoom factor
  * `disp::Bool`: display plot or just return the PlotX struct
