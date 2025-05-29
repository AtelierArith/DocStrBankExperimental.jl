```
result::StatsBase.Histogram =
    bin_cmd_smooth(colors,
                   mags,
                   color_err,
                   mag_err;
                   weights = ones(promote_type(eltype(colors), eltype(mags)),
                                  size(colors)),
                   edges   = nothing,
                   xlim    = extrema(colors),
                   ylim    = extrema(mags),
                   nbins   = nothing,
                   xwidth  = nothing,
                   ywidth  = nothing)
```

Returns a `StatsBase.Histogram` type containing the Hess diagram where the points have been smoothed using a 2D asymmetric Gaussian with widths given by the provided `color_err` and `mag_err` and weighted by the given `weights`. These arrays must all be equal in size. This is akin to a KDE where each point is broadened by its own probability distribution. Keyword arguments are as explained in [`bin_cmd_smooth`](@ref) and [`StarFormationHistories.calculate_edges`](@ref). To plot this with `PyPlot` you should do `plt.imshow(result.weights', origin="lower", ...)`.

Recommended usage is to make a histogram of your observational data using [`bin_cmd`](@ref), then pass the resulting histogram bins through using the `edges` keyword to [`bin_cmd_smooth`](@ref) and [`partial_cmd_smooth`](@ref) to construct smoothed isochrone models. 
