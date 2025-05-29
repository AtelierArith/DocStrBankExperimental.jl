```
multi_adjacency_matrix_triangulation(D::DeltaComplex) :: Matrix{Int32}
```

`D`によって定義された三角形分割の多重グラフの*隣接行列*を計算します。

$$
i,j
$$

-thのエントリは、これら2つの点を接続するエッジの数を示します。

[`adjacency_matrix_triangulation`](@ref)も参照してください。
