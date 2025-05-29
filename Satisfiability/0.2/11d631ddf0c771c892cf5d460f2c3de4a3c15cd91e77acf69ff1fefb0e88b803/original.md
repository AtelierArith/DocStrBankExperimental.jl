```
ite(x::BoolExpr, y::AbstractExpr, z::AbstractExpr)
```

If-then-else statement. When x, y, and z are Bool, equivalent to `or(x ∧ y, ¬x ∧ z)`. Note that `y` and `z` may be other expression types. For example, given the variables `BoolExpr z` and `IntExpr a`, Satisfiability.jl rewrites `z + a` as `ite(z, 1, 0) + a`.
