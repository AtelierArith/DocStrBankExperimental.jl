```
vare = hrv_class(ve,rangeset)
```

Generate a vector containing residual variances from a vector of heterogeneous residual variances `ve` and a set of ranges `rangeset`.

```juliadoctests
julia> vare = hrv_class([10.0,20.0],[3:5,6:9])
7-element Vector{Float64}:
10.0
10.0
10.0
20.0
20.0
20.0
20.0
```
