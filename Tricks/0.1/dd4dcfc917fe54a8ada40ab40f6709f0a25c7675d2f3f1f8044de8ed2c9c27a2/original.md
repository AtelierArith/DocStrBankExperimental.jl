```
static_method_count(f, [type_tuple::Type{<:Tuple])
static_method_count(@nospecialize(f)) = _static_methods(Main, f, Tuple{Vararg{Any}})
```

Returns `length(methods(f, tt))` but runs at compile-time (and does not accept a worldage argument).
