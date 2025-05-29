```
indices = get_elemental_variables(expr_tree)
```

`expr_tree` に現れる変数の `indices` を返します。この関数は、要素関数の式ツリーから要素変数を見つけるために使用されます。 `expr_tree` は `Expr`、`Type_expr_tree` または `Complete_expr_tree` である可能性があります。

例:

```julia
julia> get_elemental_variables(:(x[1] + x[3]) )
[1, 3]
julia> get_elemental_variables(:(x[1]^2 + x[6] + x[2]) )
[1, 6, 2]
```
