```
add_supports(pref::GeneralVariableRef,
             supports::Union{Real, Vector{<:Real}})::Nothing
```

Add the support points `supports` to a single infinite parameter `pref`. An `ArgumentError` is thrown if `pref` is not an independent infinite parameter.
