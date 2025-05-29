```
struct Quantity{T,D,U} <: AbstractQuantity{T,D,U}
```

A concrete subtype of [`Unitful.AbstractQuantity`](@ref).

The type parameter `T` represents the numeric backing type. The type parameters `D ::` [`Unitful.Dimensions`](@ref) and `U <:` [`Unitful.Units`](@ref).
