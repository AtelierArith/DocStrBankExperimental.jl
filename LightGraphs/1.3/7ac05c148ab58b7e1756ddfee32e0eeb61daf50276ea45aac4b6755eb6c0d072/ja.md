```
periphery(eccentricities)
periphery(g, distmx=weights(g))
```

グラフとオプションの距離行列、または事前に計算された偏心度のベクトルを与えると、グラフの直径に等しい偏心度を持つすべての頂点の集合を返します（つまり、最大の偏心度を持つ頂点の集合です）。

# 例

```jldoctest
julia> using LightGraphs

julia> periphery(star_graph(5))
4-element Array{Int64,1}:
 2
 3
 4
 5

julia> periphery(path_graph(5))
2-element Array{Int64,1}:
 1
 5
```
