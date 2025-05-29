```
JuMP.set_name(vref::DecisionVariableRef, name::String)::Nothing
```

`JuMP.set_name`を拡張して、意思決定変数の名前を設定します。

**例**

```julia-repl
julia> set_name(vref, "var_name")

julia> name(vref)
"var_name"
```
