```
ExprWOptions{E}(; lhs::E, options::NamedTupleExpr)
ExprWOptions{E}(; inner_expr::AssignExpr{E, NamedTupleExpr})
ExprWOptions(lhs::E, options::NamedTupleExpr; allow_kw::Bool=false)
```

Matches an expression of the form `lhs = (key1=value1, ...)` or `lhs`, where `lhs` matches `E`

The underlying options in the expression can be accessed/iterated over/modified via the `Base.haskey`, `Base.keys`, `BAse.iterate`, `Base.getindex`, and `Base.setindex!` functions.
