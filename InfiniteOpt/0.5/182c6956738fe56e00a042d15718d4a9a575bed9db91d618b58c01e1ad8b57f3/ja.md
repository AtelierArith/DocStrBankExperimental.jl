```
UniDistributionDomain{T <: Distributions.UnivariateDistribution} <: InfiniteScalarDomain
```

無限のパラメータを特徴付ける分布を格納する `DataType` です。これは [`IndependentParameter`](@ref) と一緒に使用されます。

**フィールド**

  * `distribution::T` ランダムパラメータの分布。
