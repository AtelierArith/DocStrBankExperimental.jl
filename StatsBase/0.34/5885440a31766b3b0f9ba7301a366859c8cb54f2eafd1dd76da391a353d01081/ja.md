```
sem(x; mean=nothing)
sem(x::AbstractArray[, weights::AbstractWeights]; mean=nothing)
```

コレクション `x` の平均の標準誤差を返します。事前に計算された `mean` を提供することができます。

重みを使用しない場合、これは（サンプル）標準偏差をサンプルサイズの平方根で割ったものです。重みが使用される場合、サンプル平均の分散は次のように計算されます：

  * `AnalyticWeights`: 実装されていません。
  * `FrequencyWeights`: $\frac{\sum_{i=1}^n w_i (x_i - \bar{x_i})^2}{(\sum w_i) (\sum w_i - 1)}$
  * `ProbabilityWeights`: $\frac{n}{n-1} \frac{\sum_{i=1}^n w_i^2 (x_i - \bar{x_i})^2}{\left( \sum w_i \right)^2}$

標準誤差は、上記の量の平方根です。

# 参考文献

Carl-Erik Särndal, Bengt Swensson, Jan Wretman (1992). Model Assisted Survey Sampling. New York: Springer. pp. 51-53.
