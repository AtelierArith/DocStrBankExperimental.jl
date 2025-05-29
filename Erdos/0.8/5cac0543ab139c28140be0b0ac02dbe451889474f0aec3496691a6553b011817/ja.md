```
digraph{G<:AGraph}(n, edgelist::Vector{Tuple{Int,Int}},
    G = Graph)
```

`n` 頂点、タイプ `G`、および指定された `edgelist` を持つ有向グラフを構築します。
