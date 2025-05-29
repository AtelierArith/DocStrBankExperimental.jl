```
rcall(r::RExpr)
```

Reduce式を評価します。

## 例

```julia-repl
julia> R"int(sin(x), x)" |> RExpr |> rcall
 - cos(x)
```
