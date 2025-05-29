```
tensor_product(g, h)
```

`g` と `h` の [テンソル積](https://en.wikipedia.org/wiki/Tensor_product_of_graphs) を返します。

### 実装ノート

入力グラフの eltype を保持します。生成されたグラフの頂点数が eltype を超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = tensor_product(star_graph(3), path_graph(3))
{9, 8} 無向単純 Int64 グラフ

julia> collect(edges(g))
8-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 5
 Edge 1 => 8
 Edge 2 => 4
 Edge 2 => 6
 Edge 2 => 7
 Edge 2 => 9
 Edge 3 => 5
 Edge 3 => 8
```
