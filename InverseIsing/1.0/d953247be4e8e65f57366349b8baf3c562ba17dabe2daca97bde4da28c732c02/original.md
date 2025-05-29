```
trans(dict::AbstractDict, len::Int64)
```

Convert from dictionary `dict` to adjacency matrix with size `len` × `len`.

# Examples

```jldoctest
julia> d = Dict((1, 2) => 5, (2, 3) => -1)

julia> trans(d, 4)
4×4 Array{Float64,2}:
 0.0   5.0   0.0  0.0
 5.0   0.0  -1.0  0.0
 0.0  -1.0   0.0  0.0
 0.0   0.0   0.0  0.0
```
