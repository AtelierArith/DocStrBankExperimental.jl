```
result::StatsBase.Histogram =
   bin_cmd(colors::AbstractVector{<:Number},
           mags::AbstractVector{<:Number};
           weights::AbstractVector{<:Number} = ones(promote_type(eltype(colors),
                                                    eltype(mags)), size(colors)),
           edges  = nothing,
           xlim   = extrema(colors),
           ylim   = extrema(mags),
           nbins  = nothing,
           xwidth = nothing,
           ywidth = nothing)
```

Returns a `StatsBase.Histogram` type containing the Hess diagram from the provided x-axis photometric `colors` and y-axis photometric magnitudes `mags`. These must all be vectors equal in length. You can either specify the bin edges directly via the `edges` keyword (e.g., `edges = (range(-0.5, 1.6, length=100), range(17.0, 26.0, length=100))`), or you can set the x- and y-limits via `xlim` and `ylim` and the number of bins as `nbins`, or you can omit `nbins` and instead pass the bin width in the x and y directions, `xwidth` and `ywidth`. See below for more info on the keyword arguments. To plot this with `PyPlot.jl` you should do `PyPlot.imshow(permutedims(result.weights), origin="lower", extent=(extrema(result.edges[1])..., extrema(result.edges[2]), kws...)` where `kws...` are any other keyword arguments you wish to pass to `PyPlot.imshow`.

# Keyword Arguments

  * `weights::AbstractVector{<:Number}` is a array of length equal to `colors` and `mags` that contains the probabilistic weights associated with each point. This is passed to `StatsBase.fit` as `StatsBase.Weights(weights)`. The following keyword arguments are passed to [`StarFormationHistories.calculate_edges`](@ref) to determine the bin edges of the histogram.
  * `edges` is a tuple of ranges defining the left-side edges of the bins along the x-axis (edges[1]) and the y-axis (edges[2]). Example: `(-1.0:0.1:1.5, 22:0.1:27.2)`. If `edges` is provided, `weights` is the only other keyword that will be read; `edges` supercedes the other construction methods.
  * `xlim` is a length-2 indexable object (e.g., a vector or tuple) giving the lower and upper bounds on the x-axis corresponding to the provided `colors` array. Example: `[-1.0, 1.5]`. This is only used if `edges` is not provided.
  * `ylim` is like `xlim` but  for the y-axis corresponding to the provided `mags` array. Example `[25.0, 20.0]`. This is only used if `edges` is not provided.
  * `nbins::NTuple{2, <:Integer}` is a 2-tuple of integers providing the number of bins to use along the x- and y-axes. This is only used if `edges` is not provided.
  * `xwidth` is the bin width along the x-axis for the `colors` array. This is only used if `edges` and `nbins` are not provided. Example: `0.1`.
  * `ywidth` is like `xwidth` but for the y-axis corresponding to the provided `mags` array. Example: `0.1`.
