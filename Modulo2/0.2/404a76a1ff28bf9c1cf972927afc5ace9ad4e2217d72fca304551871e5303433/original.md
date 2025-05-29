```
ZZ2Vector <: AbstractVector{ZZ2}
ZZ2Matrix <: AbstractMatrix{ZZ2}
ZZ2Array{N} <: AbstractArray{ZZ2,N}
```

An abstract vector / matrix / array type with elements of type `ZZ2`.

The internal representation is packed, meaning that each element only uses one bit. However, columns are internally padded to a length that is a multiple of 256.

A `ZZ2Array` can be created from any `AbstractArray` whose elements can be converted to `ZZ2`. One can also leave the elements undefined by using the `undef` argument.

See also [`zeros`](@ref), [`ones`](@ref), [`zz2vector`](@ref), [`resize!`](@ref), [`det`](@ref), [`inv`](@ref), [`rank`](@ref), [`rcef`](@ref), [`rref`](@ref).

# Examples

```jldoctest
julia> ZZ2Matrix([1 2 3; 4 5 6])
2×3 ZZ2Matrix:
 1  0  1
 0  1  0

julia> v = ZZ2Vector(undef, 2); v[1] = true; v[2] = 2.0; v
2-element ZZ2Vector:
 1
 0
```
