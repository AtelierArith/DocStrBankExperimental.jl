```
standardize(DT, X; dims=nothing, kwargs...)
```

Return a standardized copy of vector or matrix `X` along dimensions `dims` using transformation `DT` which is a subtype of `AbstractDataTransform`:

  * `ZScoreTransform`
  * `UnitRangeTransform`

# Example

```jldoctest
julia> using StatsBase

julia> standardize(ZScoreTransform, [0.0 -0.5 0.5; 0.0 1.0 2.0], dims=2)
2×3 Matrix{Float64}:
  0.0  -1.0  1.0
 -1.0   0.0  1.0

julia> standardize(UnitRangeTransform, [0.0 -0.5 0.5; 0.0 1.0 2.0], dims=2)
2×3 Matrix{Float64}:
 0.5  0.0  1.0
 0.0  0.5  1.0
```
