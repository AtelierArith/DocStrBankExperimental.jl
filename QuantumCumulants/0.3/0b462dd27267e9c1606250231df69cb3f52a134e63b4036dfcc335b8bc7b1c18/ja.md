```
NumberedOperator <: QSym
```

数値に関連付けられた演算子を定義します。交換子関係は、これらの数値を使用して計算され、特定のインデックス値の一種として機能します。

# フィールド:

  * op: [`Transition`](@ref)、[`Destroy`](@ref)、または[`Create`](@ref)のいずれかの演算子を定義できます。
  * numb: 整数の数値。
