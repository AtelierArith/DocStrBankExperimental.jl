```
SimpleQuantityArray{T}(::AbstractQuantityArray) where {T<:Number}
```

Construct a `SimpleQuantityArray{T}` with specified type `T` from a physical quantity of any implementation of `AbstractQuantityArray`.

See `SimpleQuantityArray(::AbstractQuantityArray)` for details.

# Raises Exceptions

  * `InexactError`: if the value of `AbstractQuantityArray` cannot be

represented as type `Array{T}`.
