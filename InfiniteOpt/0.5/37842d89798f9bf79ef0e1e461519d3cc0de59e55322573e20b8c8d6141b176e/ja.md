```
JuMP.unfix(vref::UserDecisionVariableRef)::Nothing
```

`JuMP.unfix`を拡張して`vref`の固定を解除します。固定されていない場合はエラーになります。

**例**

```julia-repl
julia> unfix(vref)

julia> is_fixed(vref)
false
```
