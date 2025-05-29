```
closeness_centrality(g, distmx=weights(g); normalize=true)
```

グラフ `g` の[接近中心性](https://en.wikipedia.org/wiki/Centrality#Closeness_centrality)を計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返します。

### オプション引数

  * `normalize=true`: true の場合、各ノード `n` の中心性値を $\frac{|δ_n|}{|V|-1}$ で正規化します。ここで、$δ_n$ はノード `n` から到達可能な頂点の集合です。

# 例

```jldoctest
julia> using LightGraphs

julia> closeness_centrality(star_graph(5))
5-element Array{Float64,1}:
 1.0
 0.5714285714285714
 0.5714285714285714
 0.5714285714285714
 0.5714285714285714

julia> closeness_centrality(path_graph(4))
4-element Array{Float64,1}:
 0.5
 0.75
 0.75
 0.5
```
