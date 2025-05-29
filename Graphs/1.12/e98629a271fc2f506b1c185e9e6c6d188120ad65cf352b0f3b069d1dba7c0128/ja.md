```
indegree(g[, v])
```

グラフ `g` の各頂点に終わるエッジの数に対応するベクトルを返します。`v` が指定されている場合は、`v` の頂点に対する次数のみを返します。

# 例

```jldoctest
julia> using Graphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> indegree(g)
3-element Vector{Int64}:
 1
 0
 1
```
