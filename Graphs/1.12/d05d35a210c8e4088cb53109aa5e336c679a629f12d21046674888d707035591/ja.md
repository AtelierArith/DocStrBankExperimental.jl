```
stress_centrality(g[, vs])
stress_centrality(g, k)
```

グラフ `g` のすべての頂点、指定された頂点のサブセット `vs`、またはランダムな `k` 頂点のサブセットにわたる [ストレス中心性](http://med.bioinf.mpi-inf.mpg.de/netanalyzer/help/2.7/#stressDist) を計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返します。

頂点 $n$ のストレス中心性は、$n$ を通過する最短経路の数として定義されます。

### 参考文献

  * Barabási, A.L., Oltvai, Z.N.: ネットワーク生物学: 細胞の機能的組織を理解する。Nat Rev Genet 5 (2004) 101-113
  * Shimbel, A.: 通信ネットワークの構造的パラメータ。Bull Math Biophys 15 (1953) 501-507。

# 例

```jldoctest
julia> using Graphs

julia> stress_centrality(star_graph(3))
3-element Vector{Int64}:
 2
 0
 0

julia> stress_centrality(cycle_graph(4))
4-element Vector{Int64}:
 2
 2
 2
 2
```
