```
@test_expr <expr> == <expr>
```

Test if two expression is equivalent semantically, this uses `compare_expr` to decide if they are equivalent, ignores things such as `LineNumberNode` generated `Symbol` in `Expr(:curly, ...)` or `Expr(:where, ...)`.

!!! note
    This macro requires one `using Test` to import the `Test` module name.

