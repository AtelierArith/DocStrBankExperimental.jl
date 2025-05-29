```
trans(dict::AbstarctDict)
```

Convert from dictionary `dict` to adjacency matrix.

# Example

```jldoctest
julia> d = Dict((1, 2) => -10, (2, 3) => -5, (4, 2) => 1)

julia> trans(d)
4×4 Array{Float64,2}:
   0.0  -10.0   0.0  0.0
 -10.0    0.0  -5.0  1.0
   0.0   -5.0   0.0  0.0
   0.0    1.0   0.0  0.0
```
