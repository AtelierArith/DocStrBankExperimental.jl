```
localexpect(op, state)
```

演算子 `op` が状態の局所ヒルベルト空間に作用する期待値を計算します。結果は入力状態と同じ格子を持つ `LatticeValue` です。

## 引数

  * `op`: 演算子を表す `DataOperator`。
  * `state`: 波動関数を表す `Ket` または `Bra`、または密度行列を表す `Operator`。
