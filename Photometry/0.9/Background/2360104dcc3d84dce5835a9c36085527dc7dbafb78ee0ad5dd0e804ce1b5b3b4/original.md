```
MADStdRMS()
```

Uses the standard median absolute deviation (MAD) statistic for background RMS estimation.

This is typically given as

$σ ≈ 1.4826 ⋅ \mathrm{MAD}$

# Examples

```jldoctest
julia> data = ones(3, 5);

julia> MADStdRMS()(data)
0.0

julia> MADStdRMS()(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
