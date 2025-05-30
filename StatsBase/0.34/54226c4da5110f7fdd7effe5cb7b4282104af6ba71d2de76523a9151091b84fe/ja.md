```
cov(X, w::AbstractWeights, vardim=1; mean=nothing, corrected=false)
```

重み付き共分散行列を計算します。`var`や`std`と同様に、バイアスのある共分散行列（`corrected=false`）は、`scattermat(X, w)`に$\frac{1}{\sum{w}}$を掛けて正規化することで計算されます。しかし、バイアスのない共分散行列（`corrected=true`）は、使用される重みの種類に依存します：

  * `AnalyticWeights`: $\frac{1}{\sum w - \sum {w^2} / \sum w}$
  * `FrequencyWeights`: $\frac{1}{\sum{w} - 1}$
  * `ProbabilityWeights`: $\frac{n}{(n - 1) \sum w}$ ここで、$n$は`count(!iszero, w)`に等しい
  * `Weights`: `ArgumentError`（バイアス補正はサポートされていません）
