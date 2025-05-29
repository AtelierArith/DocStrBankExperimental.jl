```
clique_percolation(g, k=3)
```

クリーク浸透アルゴリズムを使用したコミュニティ検出。コミュニティは重複する可能性があります。ベクトルのベクトル `c` を返し、`c[i]` はコミュニティ `i` の頂点の集合です。パラメータ `k` は浸透に使用するクリークのサイズを定義します。

### 参考文献

  * [Palla G, Derenyi I, Farkas I J, et al.](https://www.nature.com/articles/nature03607)

# 例

```jldoctest
julia> using Graphs

julia> clique_percolation(clique_graph(3, 2))
2-element Vector{BitSet}:
 BitSet([4, 5, 6])
 BitSet([1, 2, 3])

julia> clique_percolation(clique_graph(3, 2), k=2)
1-element Vector{BitSet}:
 BitSet([1, 2, 3, 4, 5, 6])

julia> clique_percolation(clique_graph(3, 2), k=4)
BitSet[]
```
