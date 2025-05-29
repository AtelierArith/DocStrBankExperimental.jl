```
degree_centrality(g)
indegree_centrality(g)
outdegree_centrality(g)
```

グラフ `g` の[次数中心性](https://en.wikipedia.org/wiki/Centrality#Degree_centrality)を計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返します。

### オプション引数

  * `normalize=true`: true の場合、各中心性測定値を $\frac{1}{|V|-1}$ で正規化します。

# 例

```jldoctest
julia> using Graphs

julia> degree_centrality(star_graph(4))
4-element Vector{Float64}:
 1.0               
 0.3333333333333333
 0.3333333333333333
 0.3333333333333333

julia> degree_centrality(path_graph(3))
3-element Vector{Float64}:
 0.5
 1.0
 0.5
```
