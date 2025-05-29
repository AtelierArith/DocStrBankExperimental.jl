```
union(g, h)
```

グラフ `g` と `h` を結合し、すべての頂点と辺の集合の和を取るグラフを返します。

### 実装ノート

入力グラフの eltype を保持します。生成されたグラフの頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3); h = SimpleGraph(5);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 1, 3);

julia> add_edge!(h, 3, 4);

julia> add_edge!(h, 3, 5);

julia> add_edge!(h, 4, 5);

julia> f = union(g, h);

julia> collect(edges(f))
5-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 3 => 4
 Edge 3 => 5
 Edge 4 => 5
```
