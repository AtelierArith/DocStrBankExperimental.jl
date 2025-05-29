```
isomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

`G` と `H` の間の同型マッピングを生成するイテレータを返します。返されるイテレータは、`G` と `H` の一致するノードのインデックスに対応する `ig => ih` ペアを持ちます。
