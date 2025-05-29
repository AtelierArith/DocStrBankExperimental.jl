```
JuMP.name(pref::DependentParameterRef)::String
```

Extend [`JuMP.name`](@ref JuMP.name(::JuMP.VariableRef)) to return the names of infinite dependent parameters.

**Example**

```julia-repl
julia> name(pref)
"par_name"
```
