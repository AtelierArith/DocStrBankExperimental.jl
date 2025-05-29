```
fdm_central_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

与えられた導関数と精度の順序に対する中央有限差分係数を生成します。

# 引数

  * `derivative_order::Integer`: 近似する導関数の順序
  * `accuracy_order::Integer`: 希望する精度の順序（偶数でなければならない）

# 戻り値

有限差分ステンシルのための有理係数のベクター
