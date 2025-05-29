```
JuMP.name(pref::Union{IndependentParameterRef, FiniteParameterRef})::String
```

Extend the `JuMP.name` function to accomodate infinite parameters. Returns the  name string associated with `pref`.

**Example**

```julia-repl
julia> name(t)
"t"
```
