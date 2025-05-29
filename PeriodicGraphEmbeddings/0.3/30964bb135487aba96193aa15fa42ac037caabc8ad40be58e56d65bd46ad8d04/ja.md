```
PeriodicGraphEmbedding{D,T}(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell()) where {D,T}
PeriodicGraphEmbedding{D}(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell()) where D
PeriodicGraphEmbedding(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell())
```

対応する `graph` と頂点の `placement` から [`PeriodicGraphEmbedding{D,T}`](@ref) を構築します。各頂点の分数座標は行列の列に表されます。

[0, 1) の範囲外の座標は、対応するオフセットがグラフに追加されて単位セルに戻されます。

`D > 3` の場合、`cell` のオプション引数は使用されません。

!!! warning
    この関数は、`placement` の任意の要素が [0, 1) の範囲外である場合、入力 `graph` を変更します。


!!! note
    ソートされた位置を持つ [`PeriodicGraphEmbedding`](@ref) を取得するには、代わりに [`SortedPeriodicGraphEmbedding`](@ref) を使用してください。

