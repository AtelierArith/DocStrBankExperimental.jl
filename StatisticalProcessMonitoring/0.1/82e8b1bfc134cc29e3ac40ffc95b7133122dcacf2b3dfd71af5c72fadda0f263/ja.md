```
ThompsonSampling <: AbstractSampling
```

トンプソンサンプリング法を表す型です。

# フィールド

  * `β::Float64`: トンプソンサンプリングのための `Dirichlet` 分布の濃度を調整するパラメータ。

# 例

```julia
ts = ThompsonSampling(2.0)
```
