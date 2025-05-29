```
is_used(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

Return true if `pref` is used in the model or false otherwise.

**Example**

```julia-repl
julia> is_used(t)
true
```
