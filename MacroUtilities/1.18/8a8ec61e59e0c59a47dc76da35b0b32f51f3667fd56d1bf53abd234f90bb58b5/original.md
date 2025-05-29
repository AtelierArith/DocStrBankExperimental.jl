```
IfElseExpr(; [if_else_exprs], [else_expr])
```

Matches an if/if-else/if-elseif-else block

# Arguments

  * `if_else_exprs::Vector{Pair{Any,Any}} = Pair{Any, Any}[]`: Set of `condition` => `condition_expr` blocks. The first pair corresponds to the `if` statement, the rest are `elseif` statements
  * `else_expr::Any = not_provided`: The `else` statement of the block
