```
topological_genome(net::CrystalNet{D,T})::String where {D,T}
```

ネットのトポロジカルゲノムを計算します。トポロジカルゲノムはネットの不変量であり、その表現に依存しません。また、`PeriodicGraph{D}(topological_genome(net))` が `net.pge.g` と同型であるような D-周期グラフの文字列表現でもあります（`ignore_types` オプションが無効でない限り、例外があるかもしれません）。

[`TopologicalGenome`](@ref) を返します。

!!! info
    オプションは `net` 内に直接渡す必要があります。

