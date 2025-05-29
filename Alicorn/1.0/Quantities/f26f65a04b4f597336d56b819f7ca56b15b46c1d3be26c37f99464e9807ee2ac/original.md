```
Quantity{T}(::AbstractQuantity, ::InternalUnits) where {T<:Number}
Quantity{T}(::AbstractQuantity) where {T<:Number}
```

Construct a `Quantity{T}` with specified type `T` from a physical quantity of any implementation of `AbstractQuantity`.

See `Quantity(::AbstractQuantity, ::InternalUnits)` for details.

# Raises Exceptions

  * `InexactError`: if the internal value of `AbstractQuantity` cannot be

represented as type `T`.
