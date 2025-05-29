```
ArrowTypes.fromarrow(::Type{T}, x::S) => T
```

Interface method that provides a "deserialization hook" for a custom type `T` to be constructed from the native arrow type `S`. The `T` and `S` types must correspond to the definitions used in `ArrowTypes.ArrowType(::Type{T}) = S`. This is a paired method with [`ArrowTypes.toarrow`](@ref).

The default definition is `ArrowTypes.fromarrow(::Type{T}, x) = T(x)`, so if that works for a custom type already, no additional overload is necessary. A few `ArrowKind`s have/allow slightly more custom overloads for their `fromarrow` methods:

  * `ListKind{true}`: for `String` types, they may overload `fromarrow(::Type{T}, ptr::Ptr{UInt8}, len::Int) = ...` to avoid  materializing a `String`
  * `StructKind`:

      * May overload `fromarrow(::Type{T}, x...)` where individual fields are passed as separate

    positional arguments; so if my custom type `Interval` has two fields `first` and `last`, then I'd overload like  `ArrowTypes.fromarrow(::Type{Interval}, first, last) = ...`. Note the default implementation is  `ArrowTypes.fromarrow(::Type{T}, x...) = T(x...)`, so if your type already accepts all arguments in a constructor  no additional `fromarrow` method should be necessary (default struct constructors have this behavior).

      * Alternatively, may overload `fromarrowstruct(::Type{T}, ::Val{fnames}, x...)`, where `fnames` is a tuple of the

    field names corresponding to the values in `x`. This approach is useful when you need to implement deserialization  in a manner that is agnostic to the field order used by the serializer. When implemented, `fromarrowstruct` takes precedence over `fromarrow` in `StructKind` deserialization.
