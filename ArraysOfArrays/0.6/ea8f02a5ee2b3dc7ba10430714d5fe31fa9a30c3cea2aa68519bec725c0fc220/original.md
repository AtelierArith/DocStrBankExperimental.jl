```
flatview(A::AbstractArray)
flatview(A::AbstractArray{<:AbstractArray{<:...}})
```

View array `A` in a suitable flattened form. The shape of the flattened form will depend on the type of `A`. If the `A` is not a nested array, the return value is `A` itself. When no type-specific method is available, `flatview` will fall back to `Base.Iterators.flatten`.
