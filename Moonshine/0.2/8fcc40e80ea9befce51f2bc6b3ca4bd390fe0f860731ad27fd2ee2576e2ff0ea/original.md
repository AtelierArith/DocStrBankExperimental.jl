```julia
plot_tmrcas(arg; width, npoints, noprogress, kwargs...)

```

Staircase plot of time to the most recent common ancestor. Additional keywords arguments are passed directly to [`UnicodePlots.histogram`](@ref).

This function actually computes the tmrca of each recombinatoin breakpoint, which is **very** demanding, much more than simulating the graph. It is multithreaded in order to reduce computation time.

See also [`tmrca`](@ref)

# Keywords

  * `npoints` (`nrecombinations(arg) + 1`): approximate number of points at which to compute the TMRCA. By default, every recombination breakpoint is considered. Use a smaller number of points to reduce computing time.
  * `width` (`76`): width of the plot. Its default maximum value of 76 produces a 80 columns wide plot.
  * `noprogress` (`false`): hide progress meter
  * `kwargs...`: additional keywords arguments are passed directly to [`UnicodePlots.histogram`](https://github.com/JuliaPlots/UnicodePlots.jl).
