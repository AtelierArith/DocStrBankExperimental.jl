```
quotient_graph(g::PeriodicGraph)
```

`g`からオフセットのすべての指示を削除することによって単純グラフを抽出します。これは、初期セルの境界を越えていたエッジが、初期セル内にある宛先頂点の代表にソース頂点を結ぶことを意味します。

これらの修正されたエッジはループに変わる可能性があることに注意してください。

すべてのこれらのエッジを削除するには[`truncated_graph`](@ref)を、これらのエッジの一部のみを保持するには[`slice_graph`](@ref)を参照してください。
