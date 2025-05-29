```
k_corona(g, k; corenum=core_number(g))
```

グラフ `g` の k-corona における頂点のベクトルを返します。

k-corona は、k-core 内でちょうど `k` 個の隣接点を持つ頂点の部分グラフです。

### 実装ノート

平行辺や自己ループを持つグラフには未実装です。

### 参考文献

  * k-core (ブートストラップ) パーコレーションに関する複雑ネットワーク: クリティカル現象と非局所的効果, A. V. Goltsev, S. N. Dorogovtsev, および J. F. F. Mendes, Phys. Rev. E 73, 056101 (2006) http://link.aps.org/doi/10.1103/PhysRevE.73.056101

# 例

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_corona(g, 0)
1-element Vector{Int64}:
 6

julia> k_corona(g, 1)
1-element Vector{Int64}:
 1

julia> k_corona(g, 2)
4-element Vector{Int64}:
 2
 3
 4
 5

julia> k_corona(g, 3)
Int64[]
```
