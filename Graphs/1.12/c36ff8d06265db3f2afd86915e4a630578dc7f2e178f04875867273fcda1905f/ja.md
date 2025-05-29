```
betweenness_centrality(g[, vs])
betweenness_centrality(g, k)
```

グラフ `g` の [媒介中心性](https://en.wikipedia.org/wiki/Centrality#Betweenness_centrality) をすべての頂点、指定された頂点のサブセット `vs`、またはランダムな `k` 頂点のサブセットに対して計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返します。

### オプション引数

  * `normalize=true`: true の場合、グラフ内のすべてのペア間の可能な異なるパスの総数で媒介値を正規化します。無向グラフの場合、この数は $\frac{(|V|-1)(|V|-2)}{2}$ であり、有向グラフの場合は ${(|V|-1)(|V|-2)}$ です。
  * `endpoints=false`: true の場合、最短経路のカウントにエンドポイントを含めます。

媒介中心性は次のように定義されます: $bc(v) = \frac{1}{\mathcal{N}} \sum_{s \neq t \neq v} \frac{\sigma_{st}(v)}{\sigma_{st}}$。

### 参考文献

  * Brandes 2001 & Brandes 2008

# 例

```jldoctest
julia> using Graphs

julia> betweenness_centrality(star_graph(3))
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> betweenness_centrality(path_graph(4))
4-element Vector{Float64}:
 0.0
 0.6666666666666666
 0.6666666666666666
 0.0
```
