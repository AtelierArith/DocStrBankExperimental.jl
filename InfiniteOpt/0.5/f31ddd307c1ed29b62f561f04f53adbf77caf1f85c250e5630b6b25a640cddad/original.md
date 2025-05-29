```
JuMP.set_value(pref::FiniteParameterRef, value::Real)::Nothing
```

Set the value of `pref` so long as it is a finite parameter. Errors if it is an infinite parameter.

**Example**

```julia-repl
julia> set_value(cost, 27)

julia> value(cost)
27.0
```
