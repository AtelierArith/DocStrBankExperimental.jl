```
JuMP.set_lower_bound(vref::UserDecisionVariableRef, lower::Real)::Nothing
```

`JuMP.set_lower_bound`を拡張して、`InfiniteOpt`変数`vref`の下限を指定します。`vref`が固定されている場合はエラーになります。

**例**

```julia-repl
julia> set_lower_bound(vref, -1)

julia> lower_bound(vref)
-1.0
```
