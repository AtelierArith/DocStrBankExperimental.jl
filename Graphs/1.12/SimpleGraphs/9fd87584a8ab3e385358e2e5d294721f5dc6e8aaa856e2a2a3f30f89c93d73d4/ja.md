```
static_scale_free(n, m, α)
```

`n` 頂点、`m` 辺を持ち、指数 `α` の期待されるパワーロー次数分布を持つランダムグラフを生成します。

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNGシードを設定します。
  * `finite_size_correction=true`: Cho et al. によって提案された有限サイズ補正を使用するかどうかを決定します。

### パフォーマンス

時間計算量は $\mathcal{O}(|V| + |E| \log |E|)$ です。

### 参考文献

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution in scale-free networks. Phys Rev Lett 87(27):278701, 2001.
  * Chung F and Lu L: Connected components in a random graph with given degree sequences. Annals of Combinatorics 6, 125-145, 2002.
  * Cho YS, Kim JS, Park J, Kahng B, Kim D: Percolation transitions in scale-free networks under the Achlioptas process. Phys Rev Lett 103:135702, 2009.
