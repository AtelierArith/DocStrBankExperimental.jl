```
articulation(g)
```

接続グラフ `g` の[関節点](https://en.wikipedia.org/wiki/Biconnected_component)を計算し、すべてのカット頂点を含む配列を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> articulation(star_graph(5))
1-element Array{Int64,1}:
 1

julia> articulation(path_graph(5))
3-element Array{Int64,1}:
 2
 3
 4
```
