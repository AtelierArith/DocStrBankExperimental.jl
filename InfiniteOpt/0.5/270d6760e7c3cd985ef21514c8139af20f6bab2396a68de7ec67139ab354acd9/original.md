```
JuMP.lower_bound(pref::DependentParameterRef)::Number
```

Extend the `JuMP.lower_bound` function to accomodate a single dependent infinite parameter. Returns the lower bound associated with the infinite domain. Errors if such a bound is not well-defined.

**Example**

```julia-repl
julia> lower_bound(x[1])
0.0
```
