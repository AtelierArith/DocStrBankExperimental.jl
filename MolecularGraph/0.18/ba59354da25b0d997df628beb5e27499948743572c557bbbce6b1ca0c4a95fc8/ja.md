```
edgesubgraph_isomorphisms(
    g::SimpleGraph, h::SimpleGraph;
    vmatch=(g,h)->true, ematch=(g,h)->true,
    kwargs...) -> Iterator
```

`H` と `G` のエッジ誘導部分グラフの間の同型マッピングを生成するイテレータを返します。返されるイテレータは、`G` と `H` の一致するエッジのインデックスに対応する `ig => ih` ペアを持ちます。

`vmatch` と `ematch` は、一致と見なされるために必要な特徴を制御します。

一致から得られる部分グラフを構築するには、`Graphs.induced_subgraph` を参照してください。
