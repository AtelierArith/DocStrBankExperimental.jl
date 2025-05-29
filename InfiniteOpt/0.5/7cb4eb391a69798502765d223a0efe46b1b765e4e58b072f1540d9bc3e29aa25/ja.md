```
JuMP.delete_upper_bound(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.delete_upper_bound`を拡張して、`vref`の上限を削除します。上限がない場合はエラーになります。

**例**

```julia-repl
julia> delete_upper_bound(vref)

julia> has_upper_bound(vref)
false
```
