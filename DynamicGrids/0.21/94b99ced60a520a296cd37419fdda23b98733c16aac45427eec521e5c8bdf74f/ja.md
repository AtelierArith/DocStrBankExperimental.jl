```
Remove <: BoundaryCondition

Remove()
```

[`BoundaryCondition`](@ref) フラグは、グリッド境界をオーバーフローするセルに `padval` を割り当てることを指定します。 `padval` のデフォルトは `zero(eltype(grid))` ですが、[`Output`](@ref) にキーワード引数として割り当てることができます。

次のように指定します：

```julia
ruleset = Ruleset(rule; boundary=Remove())
# または
output = sim!(output, rule; boundary=Remove())
```
