```
JuMP.set_lower_bound(pref::DependentParameterRef, lower::Real)::Nothing
```

Extend the `JuMP.set_lower_bound` function to accomodate a single dependent infinite parameter. Updates the infinite domain lower bound if such an operation is supported. Infinite scalar domain extensions that seek to employ this should extend `JuMP.set_lower_bound(domain::NewType, lower::Number)`. This will call [`set_infinite_domain`](@ref) and will error if this is not well-defined. Note that existing supports will be deleted.

**Example**

```julia-repl
julia> set_lower_bound(t, -1)

julia> lower_bound(t)
-1.0
```
