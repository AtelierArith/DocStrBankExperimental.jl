```
JuMP.has_lower_bound(pref::IndependentParameterRef)::Bool
```

Extend the `JuMP.has_lower_bound` function to accomodate infinite parameters. Return true if the domain associated with `pref` has a defined lower bound or if a lower bound can be found. Extensions with user-defined infinite domain types should extend `JuMP.has_lower_bound(domain::NewType)`.

**Example**

```julia-repl
julia> has_lower_bound(t)
true
```
