```
fdm_hermite_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

関数値と導関数情報を含むエルミート型有限差分係数を生成します。

# 引数

  * `derivative_order::Integer`: 近似する導関数の次数（≥ 2でなければならない）
  * `accuracy_order::Integer`: 希望する精度の次数

      * 導関数次数 2,3,6,7,10,11... の場合: 精度次数は 4,8,12... でなければならない
      * 導関数次数 4,5,8,9,12... の場合: 精度次数は 2,6,10... でなければならない

# 戻り値

エルミート型有限差分スタンシルの有理係数のベクトル
