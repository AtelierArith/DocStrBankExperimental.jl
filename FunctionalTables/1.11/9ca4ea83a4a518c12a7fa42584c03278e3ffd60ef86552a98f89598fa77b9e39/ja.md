```julia
FunctionalTable(itr; ...)
FunctionalTable(itr, ordering_rule; cfg)

```

`NamedTuple`を返すイテラブルから`FunctionalTable`を作成します。

返される値は同じ名前を持つ必要があります（ただし、必ずしも同じ型である必要はありません）。

`ordering_rule`はソートを指定します。`VerifyOrdering`（デフォルト）、`TrustOrdering`、および`TryOrdering`コンストラクタは、`:key`または`:key => reverse`要素のタプルのタプルを受け取ります。

`cfg`は、列の要素を収集するためのシンク構成を決定します。詳細は[`SinkConfig`](@ref)を参照してください。
