```
type = get_type_tree(expr_tree)
```

Return the type of `expr_tree`. It can either be: `constant`, `linear`, `quadratic`, `cubic` or `more`. `expr_tree` may be an `Expr`, a `Type_expr_tree` or a `Complete_expr_tree`.

Example:

```julia
julia> get_type_tree(:(5+4)) == constant
true
julia> get_type_tree(:(x[1])) == linear
true
julia> get_type_tree(:(x[1]* x[2])) == quadratic
true
```
