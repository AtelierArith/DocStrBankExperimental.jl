```
AbstractCapacityVector{T} <: AbstractVector{T}
```

`AbstractCapacityVector` is the supertype of the variable-length vector types provided by this module. At present, these are `AbstractSmallVector` and `PackedVector`. Both can hold a variable number of elements up to a predefined maximal capacity. If the element type `T` is concrete, then the immutable vector types do not allocate.

See also [`AbstractSmallVector`](@ref), [`PackedVector`](@ref).
