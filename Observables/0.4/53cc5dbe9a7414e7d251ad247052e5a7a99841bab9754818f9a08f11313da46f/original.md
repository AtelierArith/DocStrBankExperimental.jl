```
obs = Observable(val)
obs = Observable{T}(val)
```

Like a `Ref`, but updates can be watched by adding a handler using [`on`](@ref) or [`map`](@ref).
