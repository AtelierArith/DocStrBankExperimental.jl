```
LocalOperator(A::AbstractMatrix, support::UnitRange{Int})
LocalOperator(A::AbstractMatrix, i::Int=0)
```

行列 `A` に対応する `LocalOperator` を、範囲 `support` で定義されたインデックス上にサポートを持つように構築します。または、デフォルトで `0` の単一インデックス `i` を使用します。
