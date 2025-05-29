```
NormalWeightedMeanPrecision{T <: Real} <: ContinuousUnivariateDistribution
```

自然パラメータでパラメータ化された正規分布：重み付き平均 `xi` と精度 `w`。

# フィールド

  * `xi::T`: 正規分布の重み付き平均。`xi` は `w * μ` として計算され、ここで `μ` は分布の平均です。
  * `w::T`: 正規分布の精度（逆分散）。
