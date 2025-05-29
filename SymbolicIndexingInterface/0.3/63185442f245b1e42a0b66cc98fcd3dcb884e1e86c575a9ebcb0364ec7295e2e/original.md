```
set_parameter!(valp, val, idx)
```

Set the parameter at index `idx` to `val` for value provider `valp`. This defaults to modifying `parameter_values(valp)`. If any additional bookkeeping needs to be performed or the default implementation does not work for a particular type, this method needs to be defined to enable the proper functioning of [`setp`](@ref).

See: [`parameter_values`](@ref)
