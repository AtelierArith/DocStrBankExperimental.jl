```
used_by_constraint(vref::DecisionVariableRef)::Bool
```

制約によって `vref` が使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_constraint(vref)
false
```
