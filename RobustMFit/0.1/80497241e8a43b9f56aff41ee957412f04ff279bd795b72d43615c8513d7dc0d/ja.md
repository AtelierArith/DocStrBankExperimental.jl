```
PTM(d::UnivariateDistribution)
```

単変量分布のモーメントにパラメータをマッピングします。推定されるパラメータの数を p とした場合、分布の最初の p 個の生モーメントを返します。モーメントの閉じた形が実装されていないため、数値積分に依存します。

# 例

```julia
d1 = Normal()
PTM(d1)
d2 = Binomial(10, 0.4)
PTM(d2)
```

有効なパラメータの数については [`nParEff`](@ref nParEff) を、モーメントからパラメータへの逆マッピングについては [`MTP`](@ref MTP) を参照してください。
