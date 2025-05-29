```
ArrowTypes.toarrow(x::T) => S
```

Interface method to perform the actual conversion from an object `x` of type `T` to the type `S`. `T` and `S` must match the types used when defining `ArrowTypes.ArrowType(::Type{T}) = S`. Hence, `S` is the natively supported arrow type that `T` desires to convert to to enable serialization. See [`ArrowTypes.ArrowType`](@ref) docs for more details. This enables custom objects to be serialized as a natively supported arrow data type.
