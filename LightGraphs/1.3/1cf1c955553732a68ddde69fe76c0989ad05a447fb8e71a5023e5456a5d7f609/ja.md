```
center(eccentricities)
center(g, distmx=weights(g))
```

グラフとオプションの距離行列、または事前計算された偏心度のベクトルを与えると、グラフの半径に等しい偏心度を持つすべての頂点の集合を返します（つまり、最小の偏心度を持つ頂点の集合です）。

# 例

```jldoctest
julia> using LightGraphs

julia> center(star_graph(5))
1-element Array{Int64,1}:
 1

julia> center(path_graph(5))
1-element Array{Int64,1}:
 3
```
