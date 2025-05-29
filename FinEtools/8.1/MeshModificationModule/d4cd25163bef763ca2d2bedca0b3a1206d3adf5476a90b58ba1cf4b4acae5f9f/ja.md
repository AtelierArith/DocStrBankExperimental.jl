```
mergenmeshes(meshes::Array{Tuple{FENodeSet{T},AbstractFESet}}, tolerance::T) where {T<:Number}
```

複数のメッシュを統合します。

メッシュは、`tolerance`のサイズのボックス内にあるノードをマージすることによって接着されます。`tolerance`がゼロに設定されている場合、ノードのマージは行われず、メッシュのノードは単に連結されます。

# 出力

マージされたノードセット`fens`と、再番号付けされた接続性を持つ有限要素セットの配列が返されます。
