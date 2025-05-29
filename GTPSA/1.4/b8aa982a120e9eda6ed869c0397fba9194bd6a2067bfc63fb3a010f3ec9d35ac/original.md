```
numtype(t::Number)
numtype(::Type{T}) where {T<:Number}
```

If a `TPS`, then returns the type of number which the `TPS`  represents. Else, returns that number type.
