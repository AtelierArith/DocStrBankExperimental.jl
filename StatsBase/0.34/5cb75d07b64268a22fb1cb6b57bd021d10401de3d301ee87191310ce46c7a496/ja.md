```
var(x::AbstractArray, w::AbstractWeights, [dim]; mean=nothing, corrected=false)
```

実数値配列 `x` の分散を計算します。オプションで次元 `dim` に対して計算できます。`x` の観測値は重みベクトル `w` を使用して重み付けされます。未修正の（`corrected=false` の場合）サンプル分散は次のように定義されます：

$$
\frac{1}{\sum{w}} \sum_{i=1}^n {w_i\left({x_i - μ}\right)^2 }
$$

ここで、$n$ は入力の長さで、$μ$ は平均です。母集団分散の無偏推定（`corrected=true` の場合）は、使用される重みのタイプに依存する係数で $\frac{1}{\sum{w}}$ を置き換えることによって計算されます：

  * `AnalyticWeights`: $\frac{1}{\sum w - \sum {w^2} / \sum w}$
  * `FrequencyWeights`: $\frac{1}{\sum{w} - 1}$
  * `ProbabilityWeights`: $\frac{n}{(n - 1) \sum w}$ ここで $n$ は `count(!iszero, w)` に等しい
  * `Weights`: `ArgumentError`（バイアス補正はサポートされていません）
