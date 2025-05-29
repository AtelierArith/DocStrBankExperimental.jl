```
separated_terms = extract_element_functions(expr_tree)
```

Return the element functions of `expr_tree` as a vector of its subexpressions. `expr_tree` may be an `Expr`, a `Type_expr_tree` or a `Complete_expr_tree`.

Example:

```julia
julia> extract_element_functions(:(x[1] + x[2] + x[3]*x[4]))
3-element Vector{Expr}:
 :(x[1])
 :(x[2])
 :(x[3] * x[4])
```
