```
histogram(x)
histogram!(x)
```

Plot a histogram.

# Arguments

  * `x`: AbstractVector of values to be binned
  * `bins::Union{Integer, Symbol, Tuple{Integer, Integer},          AbstractVector}`: Default is :auto (the Freedman-Diaconis rule). For          histogram-types, defines the approximate number of bins to aim for,          or the auto-binning algorithm to use (:sturges,          :sqrt, :rice, :scott or :fd). For fine-grained control          pass a Vector of break values, e.g. `range(minimum(x),          stop = maximum(x), length = 25)`. Aliases: (:bin, :nb,          :nbin, :nbins).
  * `weights`: Vector of weights for the values in `x`, for weighted bin counts
  * `normalize::Union{Bool, Symbol}`: Histogram normalization               mode. Possible values are: false/:none (no               normalization, default), true/:pdf (normalize to a discrete               PDF, where the total area of the bins is 1),               :probability (bin heights sum to 1) and :density (the area               of each bin, rather than the height, is equal to               the counts - useful for uneven bin sizes).               Aliases: (:norm, :normalized, :normalizes, :normed).
  * `bar_position::Symbol`: Choose from `:overlay` (default),                  `:stack`. (warning: may only be partially                  implemented). Aliases: (:bar_positions, :barpositions).
  * `bar_width::Real`:  Width of bars in data coordinates. When               `nothing`, chooses based on `x` (or `y` when               `orientation = :h`). Aliases: (:bar_widths, :barwidths).
  * `bar_edges::Bool`: Align bars to edges (true), or centers               (the default) ?.
  * `permute::Tuple{Symbol, Symbol}`: Permutes data and axis             properties of the axes given in the tuple, e.g. (:x, :y).             Aliases: (:permutes,).

# Example

```julia-repl
julia> histogram([1,2,1,1,4,3,8],bins=0:8)
julia> histogram([1,2,1,1,4,3,8],bins=0:8,weights=weights([4,7,3,9,12,2,6]))
```
