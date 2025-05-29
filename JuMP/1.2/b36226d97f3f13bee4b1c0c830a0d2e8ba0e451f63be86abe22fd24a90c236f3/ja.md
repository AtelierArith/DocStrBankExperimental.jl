```
@NLconstraint(m::Model, expr)
```

非線形式 `expr` で説明される制約を追加します。詳細は [`@constraint`](@ref) を参照してください。例えば：

```julia
@NLconstraint(model, sin(x) <= 1)
@NLconstraint(model, [i = 1:3], sin(i * x) <= 1 / i)
```
