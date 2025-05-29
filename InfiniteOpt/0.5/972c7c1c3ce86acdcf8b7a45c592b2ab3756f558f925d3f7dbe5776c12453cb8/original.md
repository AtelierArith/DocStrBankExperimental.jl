```
JuMP.set_upper_bound(pref::DependentParameterRef, upper::Real)::Nothing
```

Extend the `JuMP.set_upper_bound` function to accomodate a single dependent infinite parameter. Updates the infinite domain upper bound if such an operation is supported. Infinite scalar domain extensions that seek to employ this should extend `JuMP.set_upper_bound(domain::NewType, upper::Number)`. This will call [`set_infinite_domain`](@ref) and will error if this is not well-defined. Note that existing supports will be deleted.

**Example**

```julia-repl
julia> set_upper_bound(t, -1)

julia> upper_bound(t)
-1.0
```
