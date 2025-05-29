```
global_clustering_coefficient(g)
```

グラフ `g` の[グローバルクラスタリング係数](https://en.wikipedia.org/wiki/Clustering_coefficient)を返します。

# 例

```jldoctest
julia> using Graphs

julia> global_clustering_coefficient(star_graph(4))
0.0

julia> global_clustering_coefficient(smallgraph(:housex))
0.7894736842105263
```
