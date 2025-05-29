```
get_expect_shadow(O::MPO, shadow::ShallowShadow)
```

MPO演算子`O`の期待値を浅いシャドウを使用して計算します。

# 引数:

  * `O::MPO`: 期待値が計算されるMPO演算子。
  * `shadow::ShallowShadow`: 因子化されたシャドウオブジェクト。

# 戻り値:

期待値を`ComplexF64`（または純粋に実数の場合は`Float64`）として返します。
