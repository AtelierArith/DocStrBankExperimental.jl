```
set_state!(valp, val, idx)
```

Set the state at index `idx` to `val` for value provider `valp`. This defaults to modifying `state_values(valp)`. If any additional bookkeeping needs to be performed or the default implementation does not work for a particular type, this method needs to be defined to enable the proper functioning of [`setsym`](@ref).

See: [`state_values`](@ref)
