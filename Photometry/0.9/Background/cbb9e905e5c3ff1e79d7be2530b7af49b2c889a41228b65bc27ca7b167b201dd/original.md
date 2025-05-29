```
StdRMS()
```

Uses the standard deviation statistic for background RMS estimation.

# Examples

```jldoctest
julia> data = ones(3, 5);

julia> StdRMS()(data)
0.0

julia> StdRMS()(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
