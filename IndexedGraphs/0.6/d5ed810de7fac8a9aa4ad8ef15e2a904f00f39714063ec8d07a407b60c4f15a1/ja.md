```
edges(g::IndexedGraph, i::Integer)
```

`i`に接続されているエッジへの遅延イテレータを返します。

デフォルトでは、無秩序のエッジはソースノードと宛先ノードを昇順にソートします。必要に応じて、[`outedges`](@ref outedges(g::IndexedGraph, i::Integer))および[`inedges`](@ref inedges(g::IndexedGraph, i::Integer))を参照してください。
