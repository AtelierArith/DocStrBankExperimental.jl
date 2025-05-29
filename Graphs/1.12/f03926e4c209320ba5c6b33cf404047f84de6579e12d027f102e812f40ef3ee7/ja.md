```
local_clustering_coefficient(g, v)
local_clustering_coefficient(g, vs)
```

グラフ `g` のノード `v` の [ローカルクラスタリング係数](https://en.wikipedia.org/wiki/Clustering_coefficient) を返します。頂点のリスト `vs` が指定されている場合は、リスト内の各ノードの係数のベクトルを返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 4);

julia> add_edge!(g, 4, 1);

julia> local_clustering_coefficient(g, [1, 2, 3])
3-element Vector{Float64}:
 1.0
 1.0
 0.0
```
