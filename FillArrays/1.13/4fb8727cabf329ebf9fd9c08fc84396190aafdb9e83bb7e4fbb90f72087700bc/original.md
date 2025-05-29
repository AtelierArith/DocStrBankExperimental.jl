```
Fill{T, N, Axes} where {T,N,Axes<:Tuple{Vararg{AbstractUnitRange,N}}}
```

A lazy representation of an array of dimension `N` whose entries are all equal to a constant of type `T`, with axes of type `Axes`. Typically created by `Fill` or `Zeros` or `Ones`

# Examples

```jldoctest
julia> Fill(7, (2,3))
2×3 Fill{Int64}, with entries equal to 7

julia> Fill{Float64, 1, Tuple{UnitRange{Int64}}}(7.0, (1:2,))
2-element Fill{Float64, 1, Tuple{UnitRange{Int64}}} with indices 1:2, with entries equal to 7.0
```
