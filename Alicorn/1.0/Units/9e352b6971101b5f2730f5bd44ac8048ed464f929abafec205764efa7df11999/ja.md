```
convertToBasicSI(abstractUnit::AbstractUnit)
```

七つの基本SI単位を用いて単位を表現します。

# 出力

`(prefactor::Real, basicUnit::Unit)`

返される変数 `basicUnit` は、七つの基本SI単位（kg, m, s, A, K, mol, cd）の累乗のみを含みます。返される変数 `prefactor` は、元の単位と返された単位との関係を示す数値の前因子です。
