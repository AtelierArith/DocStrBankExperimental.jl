```
IteratorType(::Type{T})
```

Return the iterator type of a type. Overload this function to define the iterator type of a type. The function should return a type. The default implementation is `Any`. Overload this function to enable iteration utilities related to the type such as `Base.length` and `Base.eltype`. If the [`iterator`](@ref) function is defined with return type annotation, this function will be automatically overloaded.
