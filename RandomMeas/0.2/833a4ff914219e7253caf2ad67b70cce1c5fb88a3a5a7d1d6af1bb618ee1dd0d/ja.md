```
get_expect_shadow(O::MPO, shadow::DenseShadow)
```

MPO演算子`O`の期待値を密なシャドウを使用して計算します。

# 引数:

  * `O::MPO`: 期待値が計算されるMPO演算子。
  * `shadow::DenseShadow`: 密なシャドウオブジェクト。

# 戻り値:

期待値を`ComplexF64`（または純粋に実数の場合は`Float64`）として返します。
