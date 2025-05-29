```
JuMP.set_upper_bound(pref::IndependentParameterRef, lower::Real)::Nothing
```

Extend the `JuMP.set_upper_bound` function to accomodate infinite parameters. Updates the infinite domain upper bound if and only if it is an IntervalDomain. Errors otherwise. Extensions with user-defined infinite domains should extend `JuMP.set_upper_bound(domain::NewType, upper::Number)` if appropriate.

**Example**

```julia-repl
julia> set_upper_bound(t, 2)

julia> upper_bound(t)
2.0
```
