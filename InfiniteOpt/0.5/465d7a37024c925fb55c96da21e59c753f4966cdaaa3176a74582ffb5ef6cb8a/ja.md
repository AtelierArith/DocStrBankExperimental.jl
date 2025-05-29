```
IntervalDomain <: InfiniteScalarDomain
```

無限のパラメータのための下限と上限の区間境界を格納する`DataType`です。これは[`IndependentParameter`](@ref)と一緒に使用されます。

**フィールド**

  * `lower_bound::Float64` 無限パラメータの下限。
  * `upper_bound::Float64` 無限パラメータの上限。
