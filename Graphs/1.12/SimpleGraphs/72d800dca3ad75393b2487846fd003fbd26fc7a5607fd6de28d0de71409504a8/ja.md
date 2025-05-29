```
SimpleDiGraph{T}(g::AbstractGraph)
SimpleDiGraph(g::AbstractGraph)
```

任意の `AbstractGraph` からエッジを列挙することで `SimpleDiGraph` を構築します。

もし `g` が無向グラフであれば、無向エッジ `{u, v}` が存在する場合、両方の有向エッジ `(u, v)` と `(v, u)` が追加されます。
