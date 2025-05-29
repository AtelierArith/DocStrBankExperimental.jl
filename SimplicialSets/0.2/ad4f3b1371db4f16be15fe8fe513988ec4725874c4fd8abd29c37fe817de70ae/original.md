```
AddToMul{T}
```

A wrapper to turn an additive group structure defined for the type `T` into a multiplicative structure.

# Examples

```jldoctest
julia> x, y = AddToMul(2), AddToMul(3)
(2, 3)

julia> x*y
5

julia> x^2
4

julia> inv(x)
-2

julia> x/y
-1

julia> one(x)
0
```
