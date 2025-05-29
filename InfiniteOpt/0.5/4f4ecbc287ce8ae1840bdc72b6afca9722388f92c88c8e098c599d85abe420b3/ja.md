```
MultiDistributionDomain{T <: NonUnivariateDistribution} <: InfiniteArrayDomain
```

無限のパラメータのコレクションを特徴付ける分布を格納する`DataType`です。これは[`DependentParameters`](@ref)と一緒に使用されます。

**フィールド**

  * `distribution::T` ランダムパラメータの分布。
