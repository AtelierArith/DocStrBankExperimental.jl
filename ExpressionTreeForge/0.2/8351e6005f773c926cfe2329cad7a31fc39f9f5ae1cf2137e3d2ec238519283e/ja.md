```
type = get_type_tree(expr_tree)
```

`expr_tree`の型を返します。`constant`、`linear`、`quadratic`、`cubic`、または`more`のいずれかです。`expr_tree`は`Expr`、`Type_expr_tree`、または`Complete_expr_tree`である可能性があります。

例:

```julia
julia> get_type_tree(:(5+4)) == constant
true
julia> get_type_tree(:(x[1])) == linear
true
julia> get_type_tree(:(x[1]* x[2])) == quadratic
true
```
