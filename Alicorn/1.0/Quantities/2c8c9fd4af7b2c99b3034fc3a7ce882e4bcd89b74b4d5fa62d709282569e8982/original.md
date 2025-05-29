```
QuantityArray{T}(::AbstractQuantity, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractQuantity) where {T<:Number}
```

Construct a `QuantityArray{T}` with specified type `T` from a physical quantity of any implementation of `AbstractQuantity`.

See `QuantityArray(::AbstractQuantity, ::InternalUnits)` for details.

# Raises Exceptions

  * `InexactError`: if the internal value of `AbstractQuantityArray` cannot be

represented as type `Array{T}`.
