```
JuMP.set_lower_bound(pref::IndependentParameterRef, lower::Real)::Nothing
```

Extend the `JuMP.set_lower_bound` function to accomodate infinite parameters. Updates the infinite domain lower bound if such an operation is supported. Set extensions that seek to employ this should extend `JuMP.set_lower_bound(domain::NewType, lower::Number)`.

**Example**

```julia-repl
julia> set_lower_bound(t, -1)

julia> lower_bound(t)
-1.0
```
