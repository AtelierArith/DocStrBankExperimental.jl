```
minimum_spanning_tree{T<:Real}(
    g, distmx::AbstractMatrix{T} = weights(g)
)
```

接続された無向グラフ `g` に対して、隣接行列 `distmx` を持つ [クラスカルのアルゴリズム](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm) を実行し、最小全域木を計算します。含まれるエッジとその重みを含む `Vector{KruskalHeapEntry}` を返します。
