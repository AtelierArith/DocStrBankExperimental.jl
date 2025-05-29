```
permpa(X; quantile=1.0, trials=100, threshold=0.0, comparison=FlipPA.UpperEdge(), rng=default_rng())
```

データ `X` の信号ランクを、各列のエントリを置換することによって推定します。

# オプションのキーワード引数

  * `quantile` : 比較のための分位数、`default = 1.0`
  * `trials` : 実行するサインフリップ試行の数、`default = 100`
  * `threshold` : 比較のための閾値、`default = 0.0`
  * `comparison` : 使用する比較方法、`default = FlipPA.UpperEdge()`
  * `rng` : 擬似乱数生成器、`default = default_rng()`
