```
IndexedOperator <: QSym
IndexedOperator(op::Union{Transition,Create,Destroy},ind::Index)
```

インデックスに関連付けられた演算子。

# フィールド:

  * op: 演算子、[`Transition`](@ref)、[`Destroy`](@ref) または [`Create`](@ref) のいずれかを定義できます。
  * ind: 演算子が関連付けられるインデックス。
