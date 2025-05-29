```
fdm_derivative_operator([TR=Float64], derivative_order::Integer, accuracy_order::Integer, dx::TR) -> FiniteDifferenceDerivativeOperator{TR}
```

指定された導関数および精度の順序を持つ有限差分導関数演算子を作成します。

# 引数

  * `TR`: 演算子の要素タイプ
  * `derivative_order::Integer`: 導関数の順序
  * `accuracy_order::Integer`: 精度の順序
  * `dx::TR`: グリッド間隔
