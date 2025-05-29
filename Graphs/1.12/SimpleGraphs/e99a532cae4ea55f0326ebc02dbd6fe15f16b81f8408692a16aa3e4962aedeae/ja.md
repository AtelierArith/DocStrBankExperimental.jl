```
random_regular_graph(n, k)
```

`n` 頂点を持ち、各頂点の次数が `k` のランダム無向 [正則グラフ](https://en.wikipedia.org/wiki/Regular_graph) を作成します。

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNG シードを設定します。

### パフォーマンス

時間計算量はおおよそ $\mathcal{O}(nk^2)$ です。

### 実装ノート

`nk` 個の `Int` の配列を割り当て、$k > \frac{n}{2}$ の場合は次数が $n-k-1$ のグラフを生成し、その補グラフを返します。
