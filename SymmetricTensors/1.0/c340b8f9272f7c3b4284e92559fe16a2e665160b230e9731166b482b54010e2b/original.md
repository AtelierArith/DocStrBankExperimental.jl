```
unfold(ar::Array{T,N}, mode::Int)
```

Return a matrix being an unfold of `N` dimensional array in a given mode.

```jldoctest
julia> A = reshape(collect(1.:8.), 2, 2, 2);

julia> unfold(A, 1)
2×4 Array{Float64,2}:
 1.0  3.0  5.0  7.0
 2.0  4.0  6.0  8.0

julia> unfold(A, 2)
2×4 Array{Float64,2}:
 1.0  2.0  5.0  6.0
 3.0  4.0  7.0  8.0

julia> unfold(A, 3)
2×4 Array{Float64,2}:
 1.0  2.0  3.0  4.0
 5.0  6.0  7.0  8.0
```
