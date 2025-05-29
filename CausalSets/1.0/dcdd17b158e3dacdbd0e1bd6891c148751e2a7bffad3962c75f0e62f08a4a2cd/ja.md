```
bd_coef_field_from(causet, j, dim, locality[, max_cardinality]) -> Vector{Float64}
```

時空原子 `j` に適用された BD 演算子のための Benincasa-Dowker 係数フィールドを返します。結果のベクトルの長さは `j` であり、`i` 番目のエントリは時空原子 `i` の係数に対応します。
