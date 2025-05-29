```
ExponentialFamilyDistributionAttributes(basemeasure, sufficientstatistics, logpartition, support)
```

指数族のメンバーの属性を表す構造体です。

# フィールド

  * `basemeasure::B`: 指数族のメンバーの基準測度。
  * `sufficientstatistics::S`: 指数族のメンバーの十分統計量。
  * `logpartition::L`: 指数族のメンバーの対数分割（累積量）。
  * `support::P`: 指数族のメンバーのサポート。

# オプション

  * `logbasemeasure::LB`: 指数族のメンバーの基準測度の対数。

参照: [`ExponentialFamilyDistribution`](@ref), [`getbasemeasure`](@ref), [`getsufficientstatistics`](@ref), [`getlogpartition`](@ref), [`getsupport`](@ref)
