```
JuMP.lower_bound(pref::IndependentParameterRef)::Real
```

Extend the `JuMP.lower_bound` function to accomodate infinite parameters. Returns the lower bound associated with the infinite domain. Errors if such a bound is not well-defined.

**Example**

```julia-repl
julia> lower_bound(t)
0.0
```
