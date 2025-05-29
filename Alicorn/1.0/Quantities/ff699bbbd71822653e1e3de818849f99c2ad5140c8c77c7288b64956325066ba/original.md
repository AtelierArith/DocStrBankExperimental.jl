```
QuantityArray{T}(::AbstractQuantityArray, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractQuantityArray) where {T<:Number}
```

Construct a `QuantityArray{T}` with specified type `T` from a physical quantity of any implementation of `AbstractQuantityArray`.

See `QuantityArray(::AbstractQuantityArray, ::InternalUnits)` for details.

# Raises Exceptions

  * `InexactError`: if the internal value of `AbstractQuantityArray` cannot be

represented as type `Array{T}`.
