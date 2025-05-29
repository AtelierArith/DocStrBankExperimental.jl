```
 convertToBasicSIAsExponents(abstractUnit::AbstractUnit)
```

七つの基本SI単位を用いて単位を表現します。

# 出力

`(prefactor::Real, basicUnitAsExponents::BaseUnitExponents)`

返り値の変数 `basicUnitAsExponents` は、元の単位を表現するために必要な七つの基本SI単位（kg, m, s, A, K, mol, cd）の指数を示します。返り値の変数 `prefactor` は、元の単位と返された単位との関係を示す数値の前因子です。
