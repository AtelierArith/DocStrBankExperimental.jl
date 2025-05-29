```
stirling2_matrices( n :: Int64, k :: Int64 ) :: Vector{Matrix{Bool}}
```

Generates the set of matrices with `k` rows and `n` columns where rows correspond to the groups and columns are the grouped elements. A non-zero element designates that the column id is grouped into the corresponding row.

E.g.

```jldoctest
julia> stirling2_matrices( 4, 2 )
7-element Array{Array{Bool,2},1}:
 [1 1 1 0; 0 0 0 1]
 [0 0 1 0; 1 1 0 1]
 [1 1 0 0; 0 0 1 1]
 [1 0 1 0; 0 1 0 1]
 [0 1 0 0; 1 0 1 1]
 [0 1 1 0; 1 0 0 1]
 [1 0 0 0; 0 1 1 1]
```

A `DomainError` is thrown if `n ≥ k ≥ 1` is not satisfied.
