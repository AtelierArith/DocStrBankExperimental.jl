```
SortedPeriodicGraphEmbedding{T}(graph::PeriodicGraph{D}, placement::AbstractMatrix, cell::Cell=Cell()) where {D,T}
```

対応する `graph` と頂点の `placement` から [`PeriodicGraphEmbedding{D,T}`](@ref) を構築し、結果が位置によって頂点がソートされるようにします。

結果の頂点の順序を得るために使用された `placement` の列の置換も返します。

`cell` のオプション引数は `D > 3` の場合は使用されません。

!!! warning
    この関数は、`placement` の任意の要素が [0, 1) の範囲外である場合、入力 `graph` を変更します。


関連情報として [`PeriodicGraphEmbedding{D,T}(graph, placement::AbstractMatrix{T}, cell) where {D,T}`](@ref) および [`SortedPeriodicGraphEmbedding(graph, placement::AbstractMatrix, cell)`](@ref) を参照してください。 ```
