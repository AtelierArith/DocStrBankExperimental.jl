```
EquivalentPosition{T}
```

Representation of a symmetry operation in 3D, defined by a matrix multiplication and addition.

## Example

```jldoctest
julia> eq = parse(EquivalentPosition, "1-x, z, y+1/2")
-x+1,z,y+1/2

julia> eq([1//3, 0, 1//4])
3-element StaticArrays.SVector{3, Rational{Int64}} with indices SOneTo(3):
 2//3
 1//4
 1//2
```

The type parameter `T` is the numeric type used to store the symmetry operations. It should be typically either `Rational{Int}` or `Float64`.
