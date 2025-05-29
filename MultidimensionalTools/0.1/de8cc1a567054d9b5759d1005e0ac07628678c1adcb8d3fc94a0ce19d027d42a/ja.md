与えられたインデックスに基づいて、NTupleを返します。NTupleの各要素は、各次元の(min, max)タプルを表します。

```julia
julia> T = [(3, 1), (4, 5), (6, 2), (1, 1)]
4-element Array{Tuple{Int64,Int64},1}:
 (3, 1)
 (4, 5)
 (6, 2)
 (1, 1)
 
julia> findmax_indices(T)
1×2 Array{Tuple{Int64,Int64},2}:
(1, 6)  (1, 5)
```
