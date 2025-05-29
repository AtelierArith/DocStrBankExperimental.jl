```
SortedPeriodicGraphEmbedding(graph::PeriodicGraph{D}, placement::AbstractMatrix, cell::Cell=Cell()) where D
```

対応する `graph` と頂点の `placement` から [`PeriodicGraphEmbedding{D,T}`](@ref) を構築し、結果が位置によって頂点がソートされるようにします。`T` は、すべての `placement` の要素が収まるように、`Rational{Int32}`、`Rational{Int64}`、`Rational{Int128}` および `Rational{BigInt}` の中で最小の型として決定されます。

結果の頂点の順序を得るために使用された `placement` の列の順列とともに [`PeriodicGraphEmbedding`](@ref) を返します。

`cell` のオプション引数は `D > 3` の場合は使用されません。

!!! warning
    この関数は、`placement` のいずれかの要素が [0, 1) の範囲外である場合、入力 `graph` を変更します。


!!! tip
    この関数は本質的に型が不安定です。なぜなら `T` は静的に決定できないからです。`T` が大きすぎると、後の計算が遅くなる可能性があるため、これは有用です。

    パラメータを明示的に提供するには、`SortedPeriodicGraphEmbedding` コンストラクタに `SortedPeriodicGraphEmbedding{T}(graph, placement, cell)` として渡します。


関連情報として [`PeriodicGraphEmbedding{D,T}(graph, placement::AbstractMatrix{T}, cell) where {D,T}`](@ref) を参照してください。 ```
