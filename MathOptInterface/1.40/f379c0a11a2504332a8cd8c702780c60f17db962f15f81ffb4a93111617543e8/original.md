```
constant(f::AbstractFunction[, ::Type{T}]) where {T}
```

Returns the constant term of a scalar-valued function, or the constant vector of a vector-valued function.

If `f` is untyped and `T` is provided, returns `zero(T)`.
