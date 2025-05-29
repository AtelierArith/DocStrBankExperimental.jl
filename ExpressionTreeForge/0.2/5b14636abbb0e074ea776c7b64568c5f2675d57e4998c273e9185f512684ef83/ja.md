```
separated_terms = extract_element_functions(expr_tree)
```

`expr_tree`の要素関数をその部分式のベクトルとして返します。`expr_tree`は`Expr`、`Type_expr_tree`、または`Complete_expr_tree`である可能性があります。

例:

```julia
julia> extract_element_functions(:(x[1] + x[2] + x[3]*x[4]))
3-element Vector{Expr}:
 :(x[1])
 :(x[2])
 :(x[3] * x[4])
```
