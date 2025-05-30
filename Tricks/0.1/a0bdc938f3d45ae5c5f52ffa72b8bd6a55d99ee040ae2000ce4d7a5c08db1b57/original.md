```
static_methods(f, [type_tuple::Type{<:Tuple])
static_methods(@nospecialize(f)) = _static_methods(Main, f, Tuple{Vararg{Any}})
```

Like `methods` but runs at compile-time (and does not accept a worldage argument).
