```
used_by_measure(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

Return true if `pref` is used by a measure or false otherwise.

**Example**

```julia-repl
julia> used_by_measure(t)
false
```
