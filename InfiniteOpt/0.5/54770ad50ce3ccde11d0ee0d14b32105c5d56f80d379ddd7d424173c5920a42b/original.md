```
JuMP.has_upper_bound(pref::DependentParameterRef)::Bool
```

Extend the `JuMP.has_upper_bound` function to accomodate a single dependent infinite parameter. Return true if the domain associated with `pref` has a defined upper bound or if a upper bound can be found. Extensions with user-defined scalar infinite domain types should extend `JuMP.has_upper_bound(domain::NewType)`.

**Example**

```julia-repl
julia> has_upper_bound(x[1])
true
```
