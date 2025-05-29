```
complete_overload(t::Type)::Type{<:t}
```

Implement for your type `t`. The returned value should subtype `t`.

Don't call this function directly. That's what [`complete`](@ref) is for.
