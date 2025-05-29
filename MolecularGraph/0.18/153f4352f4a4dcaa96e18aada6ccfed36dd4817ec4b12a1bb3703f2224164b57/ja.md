```
remove_all_hydrogens!(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

分子からすべての水素頂点を削除します。

これは、`Graphs.rem_vertices!`に似たvmap配列を返します。
