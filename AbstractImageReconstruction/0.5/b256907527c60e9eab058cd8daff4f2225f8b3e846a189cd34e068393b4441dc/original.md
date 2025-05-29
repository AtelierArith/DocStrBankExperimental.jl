```
getindex(plan::RecoPlan{T}, name::Symbol) where {T}
```

Return the `Observable` for the `name` property of `plan`. Equivalent to `plan[name]`.
