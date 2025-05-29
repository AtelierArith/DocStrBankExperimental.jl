```
ExprWOptions(f::ExprWOptions{E}; [lhs::E], [rhs::NamedTupleExpr], [allow_kw::Bool])
```

キーワード引数によってオプションの `lhs`、`rhs`、および `allow_kw` が上書きされた `f` の新しいコピーを返します。
