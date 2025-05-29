```
getindex(var::ContextVar{T}) -> value::T
```

Return the `value` assigned to `var`.  Throw a `KeyError` if unassigned.
