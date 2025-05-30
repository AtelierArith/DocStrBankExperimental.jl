```
rand_individuals(ss, n; [method=:latin_hypercube])
```

指定されたサンプリング `method` を使用して、`ss` 探索空間内でランダムにサンプリングすることによって `n` 個の個体を生成します。サポートされている方法は次のとおりです：

  * `uniform`: 各次元に対する一様独立サンプリング
  * `latin_hypercube` (デフォルト): ラテンハイパーキューブサンプリング法を使用
