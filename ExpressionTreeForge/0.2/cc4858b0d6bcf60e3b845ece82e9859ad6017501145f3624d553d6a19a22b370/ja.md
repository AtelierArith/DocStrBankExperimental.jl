```
expr = transform_to_Expr(expr_tree)
```

`expr_tree`を`Expr`に変換します。`expr_tree`は`Type_expr_tree`または`Complete_expr_tree`である可能性があります。**警告**: この関数は、変数を`MathOptInterface.VariableIndex`として持つ`Expr`を返します。標準の`Expr`を取得するには、`transform_to_Expr_julia`を使用してください。
