```
radius(eccentricities)
radius(g, distmx=weights(g))
```

グラフとオプションの距離行列、または事前に計算された偏心度のベクトルを指定すると、グラフの最小偏心度を返します。

# 例

```jldoctest
julia> using Graphs

julia> radius(star_graph(5))
1

julia> radius(path_graph(5))
2
```
