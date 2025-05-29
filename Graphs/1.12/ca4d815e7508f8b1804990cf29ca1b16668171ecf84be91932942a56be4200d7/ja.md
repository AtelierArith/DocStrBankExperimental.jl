```
diameter(eccentricities)
diameter(g, distmx=weights(g))
```

グラフとオプションの距離行列、または事前に計算された偏心度のベクトルを指定すると、グラフの最大偏心度を返します。

# 例

```jldoctest
julia> using Graphs

julia> diameter(star_graph(5))
2

julia> diameter(path_graph(5))
4
```
