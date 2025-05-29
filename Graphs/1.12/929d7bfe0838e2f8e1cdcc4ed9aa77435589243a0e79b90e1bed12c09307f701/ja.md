```
simplecycleslength(dg::DiGraph, ceiling = 10^6)
```

与えられた有向グラフのすべてのサイクルをジョンソンのアルゴリズムを使用して検索し、サイクルの長さとサイクルの数を表すタプルを返します。

### 実装ノート

可能なサイクルの数を把握するために、有向グラフに対して関数 `maxsimplecycles(dg::DiGraph, byscc::Bool = true)` を使用します。

`ceiling` に達した場合（`ncycles = ceiling`）、出力はサイクルの長さのサブセットのみです。

### 参考文献

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# 例

```jldoctest
julia> using Graphs

julia> simplecycleslength(complete_digraph(16))
([0, 1, 1, 1, 1, 1, 2, 10, 73, 511, 3066, 15329, 61313, 183939, 367876, 367876], 1000000)

julia> simplecycleslength(wheel_digraph(16))
([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0], 1)
```
