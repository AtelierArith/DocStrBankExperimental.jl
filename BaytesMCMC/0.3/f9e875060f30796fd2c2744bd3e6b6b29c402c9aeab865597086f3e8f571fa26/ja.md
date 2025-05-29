```julia
struct MatrixTune{A<:BaytesMCMC.MatrixMetric}
```

MCMCサンプラーのための質量と共分散行列の仕様で、ユークリッドメトリックに関連しています。

# フィールド

  * `metric::BaytesMCMC.MatrixMetric`: 密な、対角または単位質量行列。
  * `shrinkage::Float64`: 共分散推定のためのシュリンクパラメータ。
