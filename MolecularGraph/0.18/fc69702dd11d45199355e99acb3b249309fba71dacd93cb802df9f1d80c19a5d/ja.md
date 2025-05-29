```
nodesubgraph_isomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

`H`と`G`のノード誘導部分グラフの間の同型マッピングを生成するイテレータを返します。返されるイテレータは、`G`と`H`の一致するノードのインデックスに対応する`ig => ih`ペアを持ちます。
