```
similarterm(x::T, head, args)
```

Returns a term that is in the same closure of nodes with type `T`, with `head` as the head and `args` as the arguments. By default this will execute `head(args...)`.

Do not overload directly, overload `similarterm(::Type{<:T}, ...)` instead.
