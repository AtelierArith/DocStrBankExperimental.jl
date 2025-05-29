```
map_simple_wmis(graph::SimpleGraph, weights::AbstractVector) -> WMISResult
```

欠陥のあるキンググラフ上の重み付きMIS問題に重み付きMIS問題をマッピングします。

!!! note
    入力結合強度とオンサイトエネルギーは << 1 でなければなりません。このメソッドはパス分解に基づく最適化を提供しません。パス分解最適化バージョンについては、[`map_graph`](@ref)を確認してください。

