```
ShortestPathTree{R<:Real}
```

単一ソース最短経路クエリの結果を格納するためのストレージで、ソースは`s`です。

# フィールド

  * `parents::Vector{Int}`: 最短`s -> v`経路における各頂点`v`の親。
  * `dists::Vector{R}`: 各頂点`v`が`s`からの距離。
