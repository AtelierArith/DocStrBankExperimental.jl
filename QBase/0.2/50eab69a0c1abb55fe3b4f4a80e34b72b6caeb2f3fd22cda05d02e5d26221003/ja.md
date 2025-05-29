```
permutation_matrices( dim :: Int64 ) :: Vector{Matrix{Bool}}
```

次元 `dim` の正方形置換行列の集合を生成します。

例えば、

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
