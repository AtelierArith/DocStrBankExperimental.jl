```
clique_percolation(g, k=3)
```

クリーク浸透アルゴリズムを使用したコミュニティ検出。コミュニティは潜在的に重複する可能性があります。コミュニティ `i` の頂点の集合を含むベクトルのベクトル `c` を返します。パラメータ `k` は浸透に使用するクリークのサイズを定義します。

### 参考文献

  * [Palla G, Derenyi I, Farkas I J, et al.](https://www.nature.com/articles/nature03607)

# 例

```jldoctest
julia> using LightGraphs

julia> clique_percolation(clique_graph(3, 2))
2-element Array{BitSet,1}:
 BitSet([4, 5, 6])
 BitSet([1, 2, 3])

julia> clique_percolation(clique_graph(3, 2), k=2)
1-element Array{BitSet,1}:
 BitSet([1, 2, 3, 4, 5, 6])

julia> clique_percolation(clique_graph(3, 2), k=4)
0-element Array{BitSet,1}
```
