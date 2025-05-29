```
setproperty!(plan::RecoPlan{T}, name::Symbol, x::X) where {T, X}
```

Set the property `name` of `plan` to `x`. Equivalent to `plan.name = x`. Triggers callbacks attached to the property.
