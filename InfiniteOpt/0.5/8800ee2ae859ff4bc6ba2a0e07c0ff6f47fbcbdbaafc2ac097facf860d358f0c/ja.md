```
JuMP.unset_integer(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.unset_integer`を拡張して、`vref`を整数変数として解除します。整数変数でない場合はエラーになります。

```julia-repl
julia> unset_integer(vref)

julia> is_integer(vref)
false
```
