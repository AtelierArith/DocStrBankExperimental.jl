```
SmallCollections.default(::Type{T}) where T -> T
SmallCollections.default(::T) where T -> T
```

Return the default value of type `T` used for filling unused elements of an `AbstractSmallVector`. This must be defined as `zero(T)` if `T` supports algebraic operations. Otherwise it can be any value of type `T`.

This function has methods for number types, bits types, `Symbol`, `AbstractChar`, `AbstractString`, `Tuple`, `NamedTuple`, `AbstractFixedVector`, `AbstractSmallVector` und `SmallBitSet`. Methods for other types must be defined explicitly.

See also `Base.isbitstype`.
