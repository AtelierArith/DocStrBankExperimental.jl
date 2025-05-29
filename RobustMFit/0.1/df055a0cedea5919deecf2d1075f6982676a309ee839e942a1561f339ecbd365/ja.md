```
NewDist(d::UnivariateDistribution, θ::Vector{Real})
```

パラメータ θ を更新して新しい分布オブジェクトを作成します。推定されないパラメータは無視されます。

# 例

```julia
d1 = Normal()
NewDist(d1, [0, 1])

d2 = Binomial(10, 0.4)
NewDist(d2, [0.7])
```
