```
biconnected_components(g) -> Vector{Vector{Edge{eltype(g)}}}
```

無向グラフ `g` の [双連結成分](https://en.wikipedia.org/wiki/Biconnected_component) を計算し、各双連結成分を含むベクトルのベクトルを返します。

パフォーマンス: 時間計算量は $\mathcal{O}(|V|)$ です。

# 例

```jldoctest
julia> using LightGraphs

julia> biconnected_components(star_graph(5))
4-element Array{Array{LightGraphs.SimpleGraphs.SimpleEdge,1},1}:
 [Edge 1 => 3]
 [Edge 1 => 4]
 [Edge 1 => 5]
 [Edge 1 => 2]

julia> biconnected_components(cycle_graph(5))
1-element Array{Array{LightGraphs.SimpleGraphs.SimpleEdge,1},1}:
 [Edge 1 => 5, Edge 4 => 5, Edge 3 => 4, Edge 2 => 3, Edge 1 => 2]
```
