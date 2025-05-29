```
fdm_dissipation_operator([TR=Float64], dissipation_order::TI, σ::TR, dx::TR) -> FiniteDifferenceDerivativeOperator{TR}
```

指定された消散次数を持つ有限差分消散演算子を作成します。

# 引数

  * `TR`: 演算子の要素型
  * `dissipation_order::Integer`: 消散演算子の次数
  * `σ::TR`: 消散係数
  * `dx::TR`: グリッド間隔
