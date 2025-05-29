```
SourceExtractorBackground()
```

This estimator returns the background of the input using the SourceExtractorBackground algorithm.

The background is calculated using a mode estimator of the form `(2.5 * median) - (1.5 * mean)`.

If `(mean - median) / std > 0.3` then the median is used and if `std = 0` then the mean is used.

# Examples

```jldoctest
julia> data = ones(3, 5);

julia> SourceExtractorBackground()(data)
1.0

julia> SourceExtractorBackground()(data, dims=1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```
