```
SimpleQuantityArray{T}(quantity::AbstractQuantity) where {T<:Number}
```

Construct a 1x1 `SimpleQuantityArray{T}` with specified type `T` from a physical quantity of any implementation of `AbstractQuantity`.

See `SimpleQuantityArray(::AbstractQuantity)` for details.

# Raises Exceptions

  * `InexactError`: if the value of `AbstractQuantity` cannot be

represented as type `Array{T}`.
