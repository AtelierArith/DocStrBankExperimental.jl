```
UncertainScalarKDE(d::KernelDensity.UnivariateKDE, values::AbstractVector{T}, range, pdf)
```

実際のデータから推定された分布によって表される経験的値。

## フィールド

  * **`distribution`**: `values` の分布に対する `UnivariateKDE` 推定。
  * **`values`**: `distribution` が推定される値。
  * **`range`**: pdf が推定される値。
  * **`pdf`**: `range` の各点における pdf の値。
