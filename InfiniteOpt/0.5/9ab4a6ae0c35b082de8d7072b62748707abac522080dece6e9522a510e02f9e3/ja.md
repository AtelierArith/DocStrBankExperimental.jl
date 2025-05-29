```
JuMP.unset_binary(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.unset_binary`を拡張して、`vref`をバイナリ変数として解除します。バイナリでない場合はエラーになります。

```julia-repl
julia> unset_binary(vref)

julia> is_binary(vref)
false
```
