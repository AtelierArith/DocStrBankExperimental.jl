```
JuMP.name(pref::DependentParameterRef)::String
```

[`JuMP.name`](@ref JuMP.name(::JuMP.VariableRef))を拡張して、無限の依存パラメータの名前を返すようにします。

**例**

```julia-repl
julia> name(pref)
"par_name"
```
