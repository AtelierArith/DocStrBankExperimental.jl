```
rcall(r::RExpr)
```

Evaluate a Reduce expression.

## Examples

```julia-repl
julia> R"int(sin(x), x)" |> RExpr |> rcall
 - cos(x)
```
