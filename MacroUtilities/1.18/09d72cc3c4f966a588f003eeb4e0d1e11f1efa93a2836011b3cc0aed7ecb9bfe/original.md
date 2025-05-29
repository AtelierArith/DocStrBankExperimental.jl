```
DocExpr{E}(; line::LineNumberNode, docstr::Union{String, Expr}, expr::E)
```

Matches a standard documented expression `expr`, e.g.,

```julia
"documentation"
expr
```
