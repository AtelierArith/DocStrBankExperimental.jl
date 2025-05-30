```
diagind(M, k::Integer=0)
```

An `AbstractRange` giving the indices of the `k`th diagonal of the matrix `M`.

See also: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# Examples

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A,-1)
2:4:6
```
