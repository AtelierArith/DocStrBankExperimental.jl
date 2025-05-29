```
condensation(g[, scc])
```

有向グラフ `g` の強連結成分 `scc` の縮約グラフを返します。`scc` が指定されていない場合は、まず強連結成分を生成します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0])
{5, 6} directed simple Int64 graph

julia> strongly_connected_components(g)
2-element Vector{Vector{Int64}}:
 [4, 5]
 [1, 2, 3]

julia> foreach(println, edges(condensation(g)))
Edge 2 => 1
```
