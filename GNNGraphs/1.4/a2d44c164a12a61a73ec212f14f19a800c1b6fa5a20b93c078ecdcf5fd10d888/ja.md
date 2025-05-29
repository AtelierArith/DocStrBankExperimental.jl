```
khop_adj(g::GNNGraph,k::Int,T::DataType=eltype(g); dir=:out, weighted=true)
```

グラフ 'g' の隣接行列 $A$ の $A^k$ を返します。
