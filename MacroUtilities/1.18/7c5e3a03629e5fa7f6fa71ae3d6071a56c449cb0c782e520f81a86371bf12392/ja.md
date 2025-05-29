```
ExprWOptions{E}(; lhs::E, options::NamedTupleExpr)
ExprWOptions{E}(; inner_expr::AssignExpr{E, NamedTupleExpr})
ExprWOptions(lhs::E, options::NamedTupleExpr; allow_kw::Bool=false)
```

`lhs = (key1=value1, ...)` または `lhs` の形式の式に一致し、ここで `lhs` は `E` に一致します。

式内の基本オプションには、`Base.haskey`、`Base.keys`、`BAse.iterate`、`Base.getindex`、および `Base.setindex!` 関数を介してアクセス/反復/変更できます。
