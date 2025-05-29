```
estimate_background(data;
    location=SourceExtractorBackground(),
    rms=StdRMS(),
    dims=:)
```

Perform scalar background estimation using the given estimators.

The value returned will be two values corresponding to the estimated background and the estimated background RMS. The dimensionality will depend on the `dims` keyword.

`location` and `rms` can be anything that is callable, for example `median`, or one of the estimators we provide in [Background Estimators](@ref).

# Examples

```jldoctest
julia> data = ones(3, 5);

julia> bkg, bkg_rms = estimate_background(data)
(1.0, 0.0)

julia> using Statistics: median

julia> bkg, bkg_rms = estimate_background(data; location=median, rms=MADStdRMS())
(1.0, 0.0)
```

# See Also

  * [Location Estimators](@ref), [RMS Estimators](@ref)
