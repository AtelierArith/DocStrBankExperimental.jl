```
JuMP.set_start_value(vref::UserDecisionVariableRef, value::Real)::Nothing
```

`JuMP.set_start_value`を拡張して、`InfiniteOpt`変数の開始値を指定します。

**例**

```julia-repl
julia> set_start_value(vref, 1)

julia> start_value(vref)
1.0
```
