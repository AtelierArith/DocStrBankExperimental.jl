```
normalize_indices!(expr_tree, vector_indices::Vector{Int})
```

Change the indices of the variables from `expr_tree` to follow the order given by `vector_indices`. It is paired with `get_elemental_variables` to define the elemental element function expression tree. `expr_tree` may be an `Expr`, a `Type_expr_tree` or a `Complete_expr_tree`.

Example:

```julia
julia> normalize_indices!(:(x[4] + x[5]), [4,5])
:(x[1] + x[2])
```
