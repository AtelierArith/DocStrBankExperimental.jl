```
permutation_matrices( dim :: Int64 ) :: Vector{Matrix{Bool}}
```

Generates the set of square permutation matrices of dimension `dim`.

E.g.

```jldoctest
julia> permutation_matrices( 3 )
6-element Array{Array{Bool,2},1}:
 [1 0 0; 0 1 0; 0 0 1]
 [1 0 0; 0 0 1; 0 1 0]
 [0 1 0; 1 0 0; 0 0 1]
 [0 0 1; 1 0 0; 0 1 0]
 [0 1 0; 0 0 1; 1 0 0]
 [0 0 1; 0 1 0; 1 0 0]
```
