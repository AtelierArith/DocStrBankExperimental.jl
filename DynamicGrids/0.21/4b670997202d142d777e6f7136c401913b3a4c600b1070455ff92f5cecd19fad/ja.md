```
Wrap <: BoundaryCondition

Wrap()
```

[`BoundaryCondition`](@ref) フラグは、境界がグリッドの反対側に戻る座標をラップします。

次のように指定します：

```julia
ruleset = Ruleset(rule; boundary=Wrap())
# または
output = sim!(output, rule; boundary=Wrap())
```
