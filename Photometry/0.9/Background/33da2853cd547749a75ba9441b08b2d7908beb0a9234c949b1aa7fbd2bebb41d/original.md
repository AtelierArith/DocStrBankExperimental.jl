```
MMMBackground(median_factor=3, mean_factor=2)
```

Estimate the background using a mode estimator of the form `median_factor * median - mean_factor * mean`. This algorithm is based on the `MMMBackground` routine originally implemented in DAOPHOT. `MMMBackground` uses factors of `median_factor=3` and `mean_factor=2` by default. This estimator assumes that contaminated sky pixel values overwhelmingly display positive departures from the true value.

# Examples

```jldoctest
julia> x = ones(3, 5);

julia> MMMBackground()(x)
1.0

julia> MMMBackground(median_factor=4, mean_factor=3)(x, dims = 1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```

# See Also

  * [`SourceExtractorBackground`](@ref)
