```
delete_supports(pref::IndependentParameterRef; 
                [label::Type{<:AbstractSupportLabel} = All])::Nothing
```

Delete the support points for `pref`. If `label != All` then delete `label` and  any supports that solely depend on it.

**Example**

```julia-repl
julia> delete_supports(t)

julia> supports(t)
ERROR: Parameter t does not have supports.
```
