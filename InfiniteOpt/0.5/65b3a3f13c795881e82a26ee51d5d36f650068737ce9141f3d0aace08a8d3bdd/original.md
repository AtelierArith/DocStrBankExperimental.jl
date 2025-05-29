```
JuMP.set_name(pref::DependentParameterRef, name::String)::Nothing
```

Extend [`JuMP.set_name`](@ref JuMP.set_name(::JuMP.VariableRef, ::String)) to set names of dependent infinite parameters.

**Example**

```julia-repl
julia> set_name(vref, "par_name")

julia> name(vref)
"para_name"
```
