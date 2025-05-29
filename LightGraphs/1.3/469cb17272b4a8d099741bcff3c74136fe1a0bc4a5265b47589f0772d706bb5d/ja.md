```
simplecyclescount(dg::DiGraph, ceiling = 10^6)
```

有向グラフ内のサイクルの数をカウントします。ジョンソンのアルゴリズムを使用します。天井値とサイクルの数の最小値を返します。

### 実装ノート

`ceiling`は、グラフ内にサイクルが多数存在する場合にメモリのオーバーロードを避けるためにあります。デフォルト値は10^6ですが、より高くしたり低くしたりすることができます。理論的なサイクルの最大数を把握するには、`maxsimplecycles(dg::DiGraph, byscc::Bool = true)`関数を使用できます。

### 参考文献

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# 例

```jldoctest
julia> simplecyclescount(complete_digraph(6))
409
```
