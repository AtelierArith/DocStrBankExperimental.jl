```
triangles(g[, v])
triangles(g, vs)
```

グラフ `g` のノード `v` の近傍にある三角形の数を返します。頂点のリスト `vs` が指定されている場合、リスト内の各ノードの三角形の数のベクトルを返します。頂点が指定されていない場合は、グラフ内の各ノードの三角形の数を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 4);

julia> add_edge!(g, 4, 1);

julia> triangles(g)
4-element Array{Int64,1}:
 1
 1
 0
 1
```
