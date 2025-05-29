```
QuasiDiagonal(V::AbstractQuasiVector)
```

Construct a matrix with `V` as its diagonal.

# Examples

```jldoctest
julia> V = [1, 2]
2-element Array{Int64,1}:
 1
 2

julia> QuasiDiagonal(V)
2×2 QuasiDiagonal{Int64,Array{Int64,1}}:
 1  ⋅
 ⋅  2
```
