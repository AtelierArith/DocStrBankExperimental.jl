```
delete_supports(prefs::AbstractArray{<:DependentParameterRef};
                [label::Type{<:AbstractSupportLabel} = All])::Nothing
```

Delete the support points for `prefs`. Errors if any of the parameters are used by a measure or if not all belong to the same set of dependent parameters. If `label != All` then that label is removed along with any supports that solely  contain that label.

**Example**

```julia-repl
julia> delete_supports(w)

```
