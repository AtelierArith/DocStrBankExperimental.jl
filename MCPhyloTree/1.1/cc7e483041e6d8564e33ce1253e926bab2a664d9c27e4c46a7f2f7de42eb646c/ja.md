```
function leave_incidence_matrix(root::G)::Matrix{Float64} where {G<:AbstractNode}
```

`root`ノードがある木の入次数行列を計算します。葉が$m$個、頂点が$n$個の木に対して、この関数は$m \times n$行列$L$を返します。ここで、$L_{ij} = 1$は頂点$j$が葉$i$から木の根までの経路上にある場合を示し、そうでない場合は$0$です。

葉の入次数行列を返します。

  * `root` : 木の根ノード
