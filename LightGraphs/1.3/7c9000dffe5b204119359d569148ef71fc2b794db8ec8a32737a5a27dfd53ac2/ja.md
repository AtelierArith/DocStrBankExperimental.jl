```
all_neighbors(g, v)
```

`g`における`v`のすべての入出力隣接点のリストを返します。無向グラフの場合、これは[`outneighbors`](@ref)と[`inneighbors`](@ref)の両方に相当します。

### 実装ノート

現在のグラフの内部構造への参照を返し、コピーは返しません。結果を変更しないでください。グラフが変更されると、動作は未定義になります：この参照の背後にある配列も変更される可能性がありますが、それは保証されません。

# 例

```jldoctest julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> all_neighbors(g, 1) 1-element Array{Int64,1}:  3

julia> all_neighbors(g, 2) 1-element Array{Int64,1}:  3

julia> all_neighbors(g, 3) 2-element Array{Int64,1}:  1  2  ```
