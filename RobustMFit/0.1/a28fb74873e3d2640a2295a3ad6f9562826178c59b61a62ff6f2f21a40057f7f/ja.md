```
getParams(d::UnivariateDistribution)
```

分布のパラメータを選択し、ベクトルとして出力します。推定されるパラメータのみが返されます。

# 例

```julia
d1 = Normal()
getParams(d1)

d2 = Binomial(10, 0.4)
getParams(d2)
```

関連情報は[`nParEff`](@ref nParEff)を参照してください。
