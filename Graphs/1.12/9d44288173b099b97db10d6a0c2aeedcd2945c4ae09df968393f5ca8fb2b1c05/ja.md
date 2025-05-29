```
degree(g[, v])
```

グラフ `g` の各頂点で始まるまたは終わるエッジの数に対応するベクトルを返します。`v` が指定されている場合は、`v` の頂点に対する次数のみを返します。有向グラフの場合、この値は入ってくるエッジと出ていくエッジの合計に等しいです。無向グラフの場合、接続されたエッジの数に等しいです。

# 例

```jldoctest
julia> using Graphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> degree(g)
3-element Vector{Int64}:
 1
 1
 2
```
