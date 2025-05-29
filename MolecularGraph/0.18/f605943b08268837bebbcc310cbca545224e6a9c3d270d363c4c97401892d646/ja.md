```
remove_hydrogens!(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

分子から以下の水素頂点を削除します：電荷がなく、未対電子がなく、特定の質量がなく、立体特異性がなく、有機重原子に結合しているもの。

これは、`Graphs.rem_vertices!`に似たvmap配列を返します。
