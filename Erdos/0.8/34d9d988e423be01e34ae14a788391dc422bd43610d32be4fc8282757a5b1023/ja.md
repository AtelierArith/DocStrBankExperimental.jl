```
graph{G<:AGraph}(n, edgelist::Vector{Tuple{Int,Int}},
    G = Graph)
```

`n` 頂点を持つグラフを、タイプ `G` で、与えられた `edgelist` で構築します。
