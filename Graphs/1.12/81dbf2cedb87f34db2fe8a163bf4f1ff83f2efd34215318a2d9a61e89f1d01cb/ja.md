```
symmetric_difference(g, h)
```

グラフ `g` に存在し、グラフ `h` には存在しないエッジ、およびその逆のエッジを持つグラフを返します。

### 実装ノート

この関数は、次数が0の頂点を持つグラフを生成する可能性があることに注意してください。入力グラフの eltype を保持します。生成されたグラフの頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3); h = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(h, 1, 3);

julia> add_edge!(h, 2, 3);

julia> f = symmetric_difference(g, h);

julia> collect(edges(f))
3-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 2 => 3
```
