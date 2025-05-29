```
cartesian_product(g, h)
```

`g` と `h` の [直積](https://en.wikipedia.org/wiki/Cartesian_product_of_graphs) を返します。

### 実装ノート

入力グラフの eltype を保持します。生成されたグラフの頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = cartesian_product(star_graph(3), path_graph(3))
{9, 12} 無向単純 Int64 グラフ

julia> collect(edges(g))
12-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 4
 Edge 1 => 7
 Edge 2 => 3
 Edge 2 => 5
 Edge 2 => 8
 Edge 3 => 6
 Edge 3 => 9
 Edge 4 => 5
 Edge 5 => 6
 Edge 7 => 8
 Edge 8 => 9
```
