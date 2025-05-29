```
TreeTransformer(tree; kwargs...)
```

このトランスフォーマーは、Börner et al.（2017）によって提案された木に基づく分割を生成します：*Measurement/simulation mismatches and multivariate data discretization in the machine learning era*。

**キーワード引数**

  * `fit_frac = 1/5` は、`fit_tree==true` の場合に木のトレーニングに使用されるデータの割合です。
  * `fit_tree = true` は、指定された `tree` をフィットさせるかどうかを示します。
