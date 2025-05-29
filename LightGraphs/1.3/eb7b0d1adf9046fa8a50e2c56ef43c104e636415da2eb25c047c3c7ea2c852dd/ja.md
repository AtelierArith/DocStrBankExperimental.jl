```
simplecycles(dg::::IsDirected)
```

与えられた有向グラフのすべてのサイクルをジョンソンのアルゴリズムを使用して計算し、返します。

### パフォーマンス

サイクルの数は頂点の数に対して指数関数的に増加するため、大きな有向グラフでは天井を持つアルゴリズム – [`simplecycles_iter`](@ref) – を使用することをお勧めします（少し遅くなります）。可能なサイクルの数を把握したい場合は、関数 `maxsimplecycles(dg::DiGraph, byscc::Bool = true)` を確認してください。限られた長さの短いサイクルのみが必要な場合は、[`simplecycles_limited_length`](@ref) の方が効率的です。

### 参考文献

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# 例

```jldoctest
julia> simplecycles(complete_digraph(3))
5-element Array{Array{Int64,1},1}:
 [1, 2]
 [1, 2, 3]
 [1, 3]
 [1, 3, 2]
 [2, 3]
```
