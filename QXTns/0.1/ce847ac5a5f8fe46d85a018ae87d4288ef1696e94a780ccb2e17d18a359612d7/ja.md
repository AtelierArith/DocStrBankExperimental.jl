```
reduce_tensor(A::AbstractArray{Elt, N}, hyper_index_groups::Array{Int64, 1})
```

与えられたハイパーエッジグループを仮定して、与えられたテンソルの次元を削減する関数。たとえば、対角行列は両方のインデックスが [1, 2] の単一のハイパーエッジグループを持ちます。

```jldoctest
julia> reduce_tensor([[1, 0] [0, 2]], [[1, 2]])
2-element Vector{Int64}:
 1
 2
```
