```
fit(UnitRangeTransform, X; dims=nothing, unit=true)
```

Fit a scaling parameters to vector or matrix `X` and return a `UnitRangeTransform` transformation object.

# Keyword arguments

  * `dims`: if `1` fit standardization parameters in column-wise fashion; if `2` fit in row-wise fashion. The default is `nothing`.
  * `unit`: if `true` (the default) shift the minimum data to zero.

# Examples

```jldoctest
julia> using StatsBase

julia> X = [0.0 -0.5 0.5; 0.0 1.0 2.0]
2×3 Matrix{Float64}:
 0.0  -0.5  0.5
 0.0   1.0  2.0

julia> dt = fit(UnitRangeTransform, X, dims=2)
UnitRangeTransform{Float64, Vector{Float64}}(2, 2, true, [-0.5, 0.0], [1.0, 0.5])

julia> StatsBase.transform(dt, X)
2×3 Matrix{Float64}:
 0.5  0.0  1.0
 0.0  0.5  1.0
```
