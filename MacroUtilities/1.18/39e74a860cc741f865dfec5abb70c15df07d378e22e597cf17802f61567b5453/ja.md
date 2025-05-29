```
DestructuredAssigmentExpr(f::DestructuredAssigmentExpr{E}; lhs_names::Vector{Symbol}, destructure_type::Symbol, rhs::E)
```

キーワード引数によってオプションの `lhs_names`、`destructure_type`、および `rhs` が上書きされた `f` の新しいコピーを返します。
