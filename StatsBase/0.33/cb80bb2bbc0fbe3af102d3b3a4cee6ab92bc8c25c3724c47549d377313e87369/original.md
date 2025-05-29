```
fit(ZScoreTransform, X; dims=nothing, center=true, scale=true)
```

Fit standardization parameters to vector or matrix `X` and return a `ZScoreTransform` transformation object.

# Keyword arguments

  * `dims`: if `1` fit standardization parameters in column-wise fashion; if `2` fit in row-wise fashion. The default is `nothing`, which is equivalent to `dims=2` with a deprecation warning.
  * `center`: if `true` (the default) center data so that its mean is zero.
  * `scale`: if `true` (the default) scale the data so that its variance is equal to one.

# Examples

```jldoctest
julia> using StatsBase

julia> X = [0.0 -0.5 0.5; 0.0 1.0 2.0]
2×3 Matrix{Float64}:
 0.0  -0.5  0.5
 0.0   1.0  2.0

julia> dt = fit(ZScoreTransform, X, dims=2)
ZScoreTransform{Float64, Vector{Float64}}(2, 2, [0.0, 1.0], [0.5, 1.0])

julia> StatsBase.transform(dt, X)
2×3 Matrix{Float64}:
  0.0  -1.0  1.0
 -1.0   0.0  1.0
```
