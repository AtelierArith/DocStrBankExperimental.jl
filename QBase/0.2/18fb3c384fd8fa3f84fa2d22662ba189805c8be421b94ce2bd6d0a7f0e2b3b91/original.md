```
n_choose_k_matrices( n :: Int64, k :: Int64 ) :: Vector{Matrix{Bool}}
```

Generates a set of `n` by `k` matrices which represent all combinations of selecting `k` columns from `n` rows.  Each column, contains a single non-zero element and `k` rows contain a non-zero element.

E.g.

```jldoctest
julia> n_choose_k_matrices( 4, 2 )
6-element Array{Array{Bool,2},1}:
 [1 0; 0 1; 0 0; 0 0]
 [1 0; 0 0; 0 1; 0 0]
 [1 0; 0 0; 0 0; 0 1]
 [0 0; 1 0; 0 1; 0 0]
 [0 0; 1 0; 0 0; 0 1]
 [0 0; 0 0; 1 0; 0 1]
```

A `DomainError` is thrown if `n ≥ k ≥ 1` is not satisfied.
