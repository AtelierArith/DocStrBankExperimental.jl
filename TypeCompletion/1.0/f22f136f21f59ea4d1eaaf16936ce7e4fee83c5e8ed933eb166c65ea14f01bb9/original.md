```
complete(t::Type)::Type{<:t}
```

Returns a subtype of `t` that may be more specific than `t`.

Don't add methods to this function. That's what [`complete_overload`](@ref) is for.
