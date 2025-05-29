```
subgraph_monomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

`H`と`G`の部分グラフ間の単射マッピングを生成します。返されるイテレータは、`G`と`H`の一致するノードのインデックスに対応する`ig => ih`ペアを持ちます。
