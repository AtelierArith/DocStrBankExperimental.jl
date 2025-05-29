```
JuMP.upper_bound(pref::DependentParameterRef)::Number
```

Extend the `JuMP.upper_bound` function to accomodate a single dependent infinite parameter. Returns the upper bound associated with the infinite domain. Errors if such a bound is not well-defined.

**Example**

```julia-repl
julia> upper_bound(x[1])
0.0
```
