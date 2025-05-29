```
to_distance_matrix(tree::T)::Array{Float64,2} where T <:AbstractNode
```

葉の集合に対して距離行列を計算します。

Floatの配列を返します。

  * `tree` : 計算に使用される木の根ノード。
