```
JuMP.delete_lower_bound(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.delete_lower_bound`を拡張して`vref`の下限を削除します。下限がない場合はエラーになります。

**例**

```julia-repl
julia> delete_lower_bound(vref)

julia> has_lower_bound(vref)
false
```
