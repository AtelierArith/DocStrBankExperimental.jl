```
SpecialIndexedTerm <: QTerm
```

[`IndexedOperator`](@ref) エンティティの乗算で、インデックス値に特別な制約があります。例えば、σᵢ²² * σⱼ²² で、制約 i ≠ j

# フィールド:

  * term: q-数項の乗算。
  * indexMapping: 項の制約を指定する [`Index`](@ref) タプルのベクター。各タプルは1つの制約と見なされます。例: (i,j) -> i ≠ j
