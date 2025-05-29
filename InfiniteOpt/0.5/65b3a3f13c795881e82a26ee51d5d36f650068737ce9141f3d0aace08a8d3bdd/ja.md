```
JuMP.set_name(pref::DependentParameterRef, name::String)::Nothing
```

[`JuMP.set_name`](@ref JuMP.set_name(::JuMP.VariableRef, ::String))を拡張して、依存する無限パラメータの名前を設定します。

**例**

```julia-repl
julia> set_name(vref, "par_name")

julia> name(vref)
"para_name"
```
