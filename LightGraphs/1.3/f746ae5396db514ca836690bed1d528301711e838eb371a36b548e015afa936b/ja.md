```
outdegree(g[, v])
```

グラフ `g` の各頂点から始まるエッジの数に対応するベクトルを返します。`v` が指定されている場合は、`v` の頂点に対する次数のみを返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> outdegree(g)
3-element Array{Int64,1}:
 0
 1
 1
```
