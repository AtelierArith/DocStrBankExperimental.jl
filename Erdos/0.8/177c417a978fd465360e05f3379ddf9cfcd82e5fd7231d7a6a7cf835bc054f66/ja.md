```
static_scale_free(n, m, α, G=Graph;
                seed=-1, finite_size_correction=true)
```

`n` 頂点、`m` 辺を持ち、指数 `α` の期待されるパワー法則度数分布を持つランダムグラフを生成します。`finite_size_correction` は、Cho et al. によって提案された有限サイズ補正を使用するかどうかを決定します。このジェネレーターは内部で `static_fitness_model` 関数を呼び出します。時間計算量は O(|V| + |E| log |E|) です。

```
static_scale_free(n, m, α_out, α_in, G=DiGraph;
                seed=-1, finite_size_correction=true)
```

ランダム有向グラフを生成します。

参考文献:

  * Goh K-I, Kahng B, Kim D: スケールフリーネットワークにおける負荷分布の普遍的な挙動。Phys Rev Lett 87(27):278701, 2001.
  * Chung F and Lu L: 与えられた次数列を持つランダムグラフの連結成分。Annals of Combinatorics 6, 125-145, 2002.
  * Cho YS, Kim JS, Park J, Kahng B, Kim D: Achlioptasプロセス下のスケールフリーネットワークにおける浸透遷移。Phys Rev Lett 103:135702, 2009.
