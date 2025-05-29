```
JuMP.has_upper_bound(pref::IndependentParameterRef)::Bool
```

Extend the `JuMP.has_upper_bound` function to accomodate infinite parameters. Return true if the domain associated with `pref` has a defined upper bound or if a upper bound can be found. Extensions with user-defined domains should extend `JuMP.has_upper_bound(domain::NewType)`.

**Example**

```julia-repl
julia> has_upper_bound(t)
true
```
