```
SimpleGraph{T}(g::AbstractGraph)
SimpleGraph(g::AbstractGraph)
```

任意の `AbstractGraph` からエッジを列挙することで `SimpleGraph` を構築します。

もし `g` が有向グラフであれば、有向エッジ `{u, v}` は、エッジ `(u, v)` または `(v, u)` のいずれかが存在する場合に追加されます。
