```
curve_point_type(::Type{<:EllipticCurve})
```

Returns the type of a curve point (a subtype of [`EllipticCurvePoint`](@ref)) for an object of type [`EllipticCurve`](@ref).

Objects of this type support `zero()`, `iszero()`, `one()`, `rand()`, `+`, `-`, `==`, `*` (by a scalar type).

Base point is returned by `one()`, and infinity point by `zero()`.
