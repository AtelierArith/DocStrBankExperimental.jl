```
JuMP.fix(vref::UserDecisionVariableRef, value::Real;
         force::Bool = false)::Nothing
```

`JuMP.fix`を拡張して、`InfiniteOpt`変数の値を固定します。`force = true`でない限り、変数に下限および/または上限がある場合はエラーになります。

**例**

```julia-repl
julia> fix(vref, 3)

julia> fix_value(vref)
3.0

julia> fix(vref2, 2, force = true)

julia> fix_value(vref2)
2.0
```
