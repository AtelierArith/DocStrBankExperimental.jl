```
JuMP.upper_bound(pref::IndependentParameterRef)::Real
```

Extend the `JuMP.upper_bound` function to accomodate infinite parameters. Returns the upper bound associated with the infinite domain. Errors if such a bound is not well-defined. Extensions with user-defined domain types should extend `JuMP.has_upper_bound(domain::NewType)` and `JuMP.upper_bound(domain::NewType)` if appropriate.

**Example**

```julia-repl
julia> upper_bound(t)
1.0
```
