```
params(d::UnivariateDistribution)
```

パラメータのタプルを返します。`d` をタイプ `D` の分布とすると、`D(params(d)...)` は $d$ と全く同じ分布を構築します。
