```
stmt_effect_flags(stmt, rt, src::Union{IRCode,IncrementalCompact}) ->
    (consistent::Bool, removable::Bool, nothrow::Bool)
```

Returns a tuple of `(:consistent, :removable, :nothrow)` flags for a given statement.
