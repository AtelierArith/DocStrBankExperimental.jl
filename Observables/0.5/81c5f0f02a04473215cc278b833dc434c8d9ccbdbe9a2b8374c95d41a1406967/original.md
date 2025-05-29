```
obs = Observable(val; ignore_equal_values=false)
obs = Observable{T}(val; ignore_equal_values=false)
```

Like a `Ref`, but updates can be watched by adding a handler using [`on`](@ref) or [`map`](@ref). Set `ignore_equal_values=true` to not trigger an event for `observable[] = new_value` if `isequal(observable[], new_value)`.
