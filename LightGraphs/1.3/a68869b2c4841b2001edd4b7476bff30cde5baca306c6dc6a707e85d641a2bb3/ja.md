```
induced_subgraph(g, vlist)
induced_subgraph(g, elist)
```

`g`の頂点`vlist`または辺`elist`によって誘導される部分グラフを返し、新しい頂点を古い頂点にマッピングするベクトルを返します（部分グラフの頂点`i`は、`g`の頂点`vmap[i]`に対応します）。

返されるグラフは`length(vlist)`の頂点を持ち、新しい頂点`i`は`vlist`の`i`番目の位置にある元のグラフの頂点に対応します。

### 使用例

```doctestjl
julia> g = complete_graph(10)

julia> sg, vmap = induced_subgraph(g, 5:8)

julia> @assert g[5:8] == sg

julia> @assert nv(sg) == 4

julia> @assert ne(sg) == 6

julia> @assert vm[4] == 8

julia> sg, vmap = induced_subgraph(g, [2,8,3,4])

julia> @assert sg == g[[2,8,3,4]]

julia> elist = [Edge(1,2), Edge(3,4), Edge(4,8)]

julia> sg, vmap = induced_subgraph(g, elist)

julia> @assert sg == g[elist]
```
