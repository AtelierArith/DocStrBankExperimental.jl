```
get(var::ContextVar{T}) -> Union{Some{T},Nothing}
```

Return `Some(value)` if `value` is assigned to `var`.  Return `nothing` if unassigned.
