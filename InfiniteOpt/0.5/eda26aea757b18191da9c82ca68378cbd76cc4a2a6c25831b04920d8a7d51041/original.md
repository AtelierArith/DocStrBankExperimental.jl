```
used_by_constraint(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

Return true if `pref` is used by a constraint or false otherwise.

**Example**

```julia-repl
julia> used_by_constraint(t)
true
```
