```
JuMP.set_upper_bound(vref::UserDecisionVariableRef, upper::Real)::Nothing
```

`JuMP.set_upper_bound`を拡張して、`InfiniteOpt`変数`vref`の上限を指定します。`vref`が固定されている場合はエラーになります。

**例**

```julia-repl
julia> set_upper_bound(vref, 1)

julia> upper_bound(vref)
1.0
```
