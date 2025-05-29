```
set_supports(pref::GeneralVariableRef, supports::Union{Real, Vector{<:Real}};
             [force::Bool = false])::Nothing
```

Set the support points associated with a single infinite parameter `pref`. An `ArgumentError` is thrown if `pref` is not an independent infinite parameter.
