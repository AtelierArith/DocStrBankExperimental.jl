```
TopologicalRelation
```

与えられた [`Topology`](@ref) に対して実装された [`Mesh`](@ref) の面の間の位相関係。

このトレイトを実装するオブジェクトは、面を表す整数インデックスで評価できる関数です。

## 例

```julia
# 境界関係マッピングを作成
# 2-面から0-面（すなわち頂点）への
∂ = Boundary{2,0}(topology)

# 最初の面の頂点のリスト
∂(1)
```

## 参考文献

  * Floriani, L. & Hui, A. 2007. [Shape representations based on simplicial and cell complexes](https://diglib.eg.org/handle/10.2312/egst.20071055.063-087)
