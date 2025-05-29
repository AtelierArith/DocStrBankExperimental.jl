```
curve_scalar_type(::Type{<:EllipticCurve})
```

Returns the type of an associated scalar for an object of type [`EllipticCurve`](@ref). All operations with objects of this type are done modulo curve order.

Objects of this type support `zero()`, `iszero()`, `one()`, `rand()`, `+`, `-`, `==`, `*` (by a scalar type or a point type), `iseven()`, `isodd()`, `>>`, `inv()`, `divrem()`, `trailing_zeros()`, `DarkIntegers.num_bits()`.
