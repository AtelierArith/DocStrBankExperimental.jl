```julia
plot_breakpoints(arg; nbins, height, kwargs...)

```

Heatmap of recombination events' positions.

See also [`breakpoints`](@ref)

# Keywords

  * `nbins` (`clamp(nrecombinations(arg) ÷ 100, 1, 69)`): number of bins. Its default maximum value of 69 produces a nice 80 columns wide plot.
  * `height` (`7`): height of the plot.
  * `kwargs...`: additional keywords arguments are passed directly to [`UnicodePlots.histogram`](https://github.com/JuliaPlots/UnicodePlots.jl).
