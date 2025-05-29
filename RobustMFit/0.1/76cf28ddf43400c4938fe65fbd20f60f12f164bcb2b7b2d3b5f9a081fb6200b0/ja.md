```
nParEff(d::UnivariateDistribution)
```

分布 `d` の推定されるパラメータの数を取得します。一部のパラメータは定数として扱われます。

# 例

```julia
d1 = Normal()
nParEff(d1)

d2 = Binomial(10, 0.4)
nParEff(d2)
```
